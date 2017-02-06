#include<iostream>
#include<stdlib.h>
using namespace std;

//Calcula y devuelve el promedio de los numeros ingresados
float Promedio(int x, int v[]){
  int acum=0;
  for(int i=0; i<x; i++)
    acum += v[i];
  return ((float)acum/x);
}

//Determina y devuelve el mayor de los numeros ingresados
int Mayor(int x, int v[]){
  int mayor=0;
  for(int i=0; mayor!=10 && i<x; i++)
    if (v[i]>mayor)
      mayor = v[i];
  return mayor;
}

//Determina y devuelve el menor de los numeros ingresados
int Menor(int x, int v[]){
  int menor=10;
  for(int i=0; menor!=1 && i<x; i++)
    if (v[i]<menor)
      menor = v[i];
  return menor;
}

//Muestra en pantalla los numeros ingresados
void NrosIngresados(int x, int v[]){
  for(int i=0; i<x; i++)
    cout << v[i] << ' ';
}

//Muestra el menu y devuelve la opcion elegida
int Menu(void){
  int x;
  cout
       << "Menu" << endl
       << "1 Calcular el promedio de los numeros ingresados" << endl
       << "2 Determinar el mayor" << endl
       << "3 Determinar el menor" << endl
       << "4 Muestra en pantalla todos los numeros ingresados" << endl
       << "5 Terminar programa" << endl
       << "**Ingresar el numero de la opcion deseada** ";
  cin >> x;
  while (x<1 || x>5){
    cout << "El numero ingresado no es valido, ingrese "
         << "nuevamente " << endl;
    cin >> x;
  }
  cout << endl;
  return x;
}

//Carga el vector y devuelve la cantidad de valores ingresados en el
int CargarVector(int v[]){
  int x, i=0;
  cout << "Ingresar hasta 100 valores del 1 al 10 para cargar un vector ingresando 0 para dejar de ingresar" << endl;
  cin >> x;
  while (x!=0 && i<100){
    while (x<1 || x>10){
      cout << "El numero ingresado no es valido, ingrese nuevamente" << endl;
      cin >> x;
    }
    v[i]=x;
    cin >> x;
    i++;
  }
  return i;
}

//Opera segun la opcion elegida y muestra el resultado en pantalla
void OperarYMostrar(int x, int v[], int op){
  switch (op){
      case 1:
        cout << "El promedio de los numeros ingresados es " << Promedio(x, v);
        break;
      case 2:
        cout << "El mayor de los numeros ingresados es " << Mayor(x, v);
        break;
      case 3:
        cout << "El menor de los numeros ingresados es " << Menor(x, v);
        break;
      case 4:
        cout << "Los numeros ingresados son: ";
        NrosIngresados(x, v);
        break;
      case 5:
        cout << "Programa terminado";
    }
    cout << endl << endl;
}

//Funcion principal
main(){
  int cantIngresada, vect[100], opc;
  cantIngresada = CargarVector(vect);
  system("cls");
  do {
    opc = Menu();
    OperarYMostrar(cantIngresada, vect, opc);
  } while (opc!=5);
  return 0;
}
