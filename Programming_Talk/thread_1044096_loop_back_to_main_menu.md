---
title: "loop back to main menu"
date: 2009-01-19
forum: Programming Talk
---

### Post by jorgeberber on 2009-01-19
hi there all , how do i loop this back to the main menu after i have use ctrl+d to give me the final total ...i looked everywhere and tried a few things but no success , my book doesnt say much either 
thanks .
int main()
{
	int end = 0;
	while(end!=1)
	{
		int op;
		system("CLS");
		op = Menu();
		switch(op)
		{
		case 1:
			funct1();
			break;
		case 2:
			funct2();
			break;
		case 3:
			funct3();
			break;
		case 4:
			funct4();
			break;
		case 5: // This is the option to quit the program
			end = 1;
			break;
		default:
			printf("ERRO: Opcao invalida.\n\n");
			system("PAUSE");
			break;
		}
	}
	return 0;
}

---

### Post by jorgeberber on 2009-01-19
sorry that was the wrong code here it is:


#include <iostream>
#include <cstdlib>
#include <cstdio>
#include <ctime>
#include <string>
#include <iomanip>
#include <ctype.h>
using namespace std;

struct CodeInfo
{
	string productCode;
	double price; // or use double if you wish
	double subtotal;
};

int main(int argc, char **argv){

		
	char choice;

	
	cout<< "SELECT DEPARTMENT:\n";
	cout<< " 1. Screens:\n" ;
	cout<< " 2. Awnings:\n" ;
	cout<< " 3. Verticals:\n" ;
	cout<< " 4. Rollers:\n";
	cout<< " 5. Venetians:\n";
	cout<< " 6. for quiting...\n";
	cin >> choice;
	
	cout<<"\n";
	
	          switch(choice){
			
			case '1':
			cout<< "SELECT PRODUCT:\n";
			cout<< " 1. Screen Door \n";
			cout<< " 2. Security Screen Door\n" ;
			cout<< " 3. CrimeSafe\n" ;
			cout<< " 6. Quit\n";		  
			cin >> choice;
	
			  }
			
			switch(choice) {
		    
			case '1': 
				    {	 	
					
					CodeInfo items[3] = { {"rb38ssw500x500", 200},{"rb38ssw600x600", 300},{"rb38ssw700x700", 400}};
					
					double subtotal;
						
					cout<< "SCREEN DOORS\n" ;
					cout<< " Please Input Sizes:\n";
					
			do {
			
				string code;
				size_t cnt = -1;
							
					cout << "Enter product code (or ctrl-D to exit): ";
					cin >> code;
							
							for (size_t i = 0; i < sizeof(items) / sizeof(CodeInfo); i++) {
								if (code == items[i].productCode) {
									cnt = i;
									cout << "setting\n";
														} 
							    }
							
							if (cnt != -1) {
							
								cout << "Price is: " << items[cnt].price << endl;
								subtotal += items[cnt].price;
							                                  } 
							
							else { 
								cout << "\nSubtotal = " <<  subtotal << endl;   //  setprecision(2) << subtotal << endl;
								break;
							           }
							
				}           while (!cin.eof());
						
						return 0;
				
	} 
				
					
				case '2' :
				          {		
					
					CodeInfo items[3] = { {"ssd500x500", 200},{"ssd600x600", 300},{"ssd700x700", 400}};
		
					
					double subtotal;
		
							  cout<< "SECURITY SCREEN DOORS\n" ;
					          cout<< " Please Input Sizes:\n";
					do {
						string code;
						size_t cnt = -1;
						
						cout << "Enter product code (or ctrl-D to exit): ";
						cin >> code;
						
						for (size_t i = 0; i < sizeof(items) / sizeof(CodeInfo); i++) {
							if (code == items[i].productCode) {
								cnt = i;
								cout << "setting\n";
							}
						}
						
						if (cnt != -1) {
							
							cout << "Price is: " << items[cnt].price << endl;
							subtotal += items[cnt].price;
						    } 
						
						else { 
							cout << "\nSubtotal = " <<  subtotal << endl;   //  setprecision(2) << subtotal << endl;
							break;
						}
						
					} while (!cin.eof()); }
					
				return 0;
						
						  }			
	

}


sorry if looks messy , im still learning

---

### Post by Zugzwang on 2009-01-19
> **jorgeberber said:**
> sorry if looks messy , im still learning

First of all, please use correct indentation in your code (a good editor will do this for you) and second, please surround your code by PHP-tags in order to make your stuff more readable.

---

### Post by jorgeberber on 2009-01-19
> **Zugzwang said:**
> First of all, please use correct indentation in your code (a good editor will do this for you) and second, please surround your code by PHP-tags in order to make your stuff more readable.



if i knew how to at first place i would ,  as i said im learning , as far as im concerned if it works is good enough....

---

