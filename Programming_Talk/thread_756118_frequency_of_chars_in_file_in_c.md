---
title: "frequency of chars in file in c"
date: 2008-04-15
forum: Programming Talk
---

### Post by thebloggu on 2008-04-15
ok sorry for boring once again but i'm tired of segfault so

[PHP]#include <stdio.h>
#include <string.h>
#include <stdlib.h>

int freq_char(char caracter, FILE *sequencia){

	char compara;

	int freq=0;

	do{

		printf("3\n");

		compara = fgetc(sequencia);

		printf("4\n");

		if(compara==caracter)
			freq++;

		printf("5\n");

	}while(compara != EOF);

	printf("6\n");

	return freq;

}



int main(){

	int freq;

	FILE *sequencia;

	printf("1\n");

	sequencia = fopen("sequencias.a","r");

	printf("2\n");

	freq = freq_char('T',sequencia);

	printf("3\n");

	return 0;

}


/*

int encontra(char *string, char caracter){

	int i=0;

	char *string_compara = string;

	while(string[i]!=caracter || string[i]!='\0'){
	
		i++;
	
	}

	if((strlen(string)!=strlen(string_compara)) && (string[i]!=caracter))
		return 1;//verdadeiro,nao existe

	else return 0;//falso,existe

}
*/


/*

int main(){

	FILE *sequencia;

	int a=0,i=0;

	char compara;

	char c = '0',d = '0',e = '0',f = '0';

	char b[4] = {c,d,e,f};

	char caracter = 'T';

	char *resultado;

	do{

		

		if(compara != c && compara != d && compara != e && compara != f){
		
			a = freq_char(caracter,sequencia);

			if(c=='0')
				c=caracter;

			else{
			
				if(d=='0')
					d=caracter;

				else{
				
					if(e=='0')
						e=caracter;

					else{
					
						if(f=='0')
							f=caracter;

						else{
						
							exit(EXIT_FAILURE);
						
						}
					
					}
				
				}
			
			}

			sprintf(resultado,"%c - %i\n",caracter,a);
		
			i++;

		}

	}while(compara!=EOF);

	printf("%s\n",resultado);

	return 0;

}


*/[/PHP]

i have this program in c and tried what is commented too but always get srgfault. my guess is a problems with pointer. i have to check all the chars that are in a file and count them. would somone help me please?

---

### Post by Can+~ on 2008-04-15
Use feof on the condition of the while.

[PHP]while(!feof(sequencia))
{

}[/PHP]

And instead of a do{}while block, use a while{}, you don't want to read a character in case the file just contains an EOF. Also, you should look if the file opened exist with (pseudocode):

[PHP]
if (FilePointer)
{
     doSomething
     closeFile
}else
    file does not exist![/PHP]

(Notice that FilePointer is NULL when there's no file or you can't read it. And NULL on an if statement is False, it's equal to FilePointer != NULL)

Y en que lenguaje están las variables?

---

### Post by mike_g on 2008-04-15
Theres nothing wrong with checking for EOF, but AFAIK EOF is an integer value.

Either way the code runs fine for me. Maybe you are looking in the wrong place for the input file or something?

---

### Post by Tuna-Fish on 2008-04-16
> **mike_g said:**
> Theres nothing wrong with checking for EOF, but AFAIK EOF is an integer value.

Either way the code runs fine for me. Maybe you are looking in the wrong place for the input file or something?

EOF is -1. Might not fit a char.

---

