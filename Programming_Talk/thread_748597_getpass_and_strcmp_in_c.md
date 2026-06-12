---
title: "getpass and strcmp in c"
date: 2008-04-07
forum: Programming Talk
---

### Post by thebloggu on 2008-04-07
```
void registo(){

	char nome_utilizador[20];
	
	char *password;
	
	int a;
	
	char *password_conf; //confirm password
	
	while(getchar()!='\n');
	
	printf("What name do you want to use? ");
	
	fgets(nome_utilizador,20,stdin);
	
	password = getpass("What password do you want to use? ");
	
	password_conf = getpass("Please confirm the password:: ");
	
	a = strcmp(password,password_conf);
	
	if(strcmp(password,password_conf)!=0){
		
		printf("Congratulations you successfully registeres in the program\n");
		
		login();
		
	}
	
	else{
		
		printf("Passwords dont match please try again\n");
		
		registo();
		
	}

}
```

i have this but strcmp doesnt work even though the words are equal. what's the problem?

---

### Post by mike_g on 2008-04-07
strcmp returns 0 if the two word match. So you should be doing:
```
if(strcmp(password,password_conf)==0){
// password matches

```

---

### Post by scourge on 2008-04-07
strcmp returns 0 when the strings are equal.

So, replace this:
```
if(strcmp(password,password_conf)!=0)
```

with this:
```
if (strcmp(password,password_conf) == 0)
```

---

### Post by thebloggu on 2008-04-07
LOL

sorry, i tried just

if(strcmp(password,password_conf)){

without == or != because i thought it was by default ==. i tried ==0 and it worked thank you

---

### Post by sq377 on 2008-04-08
sudo apt-get install manpges-dev manpages-posix-dev
man getpass

"DESCRIPTION
       This function is obsolete.  Do not use it.
"

If you want to avoid it, here is a function I used to implement it a while back:
```

	...
	#include <termios.h>
	....
	char *password = 0;
	....
	if (password == NULL)
	{
		#ifdef _GNU_SOURCE // Other operating systems hide terminals differently

		struct termios normal, hidden;

		tcgetattr(fileno(stdin), &normal);
		hidden = normal;
		hidden.c_lflag &= ~ECHO || ECHOCTL;
		tcsetattr(fileno(stdin), TCSAFLUSH, &hidden); // Terminal is hidden

		#endif // _GNU_SOURCE

		printf("Password: ");
		password = calloc(100, sizeof(char));
		password[strlen(password + 1)] = '\0';
		fgets(password, 99, stdin);
		for (x = 0; x <= 100; x++)
		{
			if (password[x] == '\n')
				password[x] = '\0';
			if (password[x] == '\0')
				break;
		}

		#ifdef _GNU_SOURCE
		printf("\n");
		tcsetattr(fileno(stdin), TCSAFLUSH, &normal);
		fflush(stdin);
		fflush(stdout);
		#endif // _GNU_SOURCE
	}
```

---

### Post by mike_g on 2008-04-08
> 		password = calloc(100, sizeof(char)); 
Personally I would not allocate memory when you know the container size (100). Also, your code never frees the memory once its done with it which  could cause memory leaks. Since calloc zeros the memory theres no need for this line:
> password[strlen(password + 1)] = '\0';
And instead of this:
> 		for (x = 0; x <= 100; x++)
		{
			if (password[x] == '\n')
				password[x] = '\0';
			if (password[x] == '\0')
				break;
		}
You could just do:
```
if(strlen(password) < 100)
    password[strlen(password)-1]='\0';

```
Apart from that the termios bit looks interesting, I have never seen it myself yet. Might have a play around with the code ;)

---

### Post by smartbei on 2008-04-08
You will actually want:
```

password[strlen(password) - 2] = '\0';

```
Since strlen(password) returns the length including the \n...In order to remove the \n you have to subtract one for the array being zero-indexed and one to delete the \n.

EDIT: This is wrong - as mike_g shows below. (Sorry, my mistake)

---

### Post by mike_g on 2008-04-08
Sorry, but I think you are wrong. Using your method the following code outputs 'Hel':
```
#include <stdio.h>
#include <string.h>

int main()
{
	char word[] = "Hello";
	word[strlen(word)-2]='\0';
	printf("%s", word);	
	return 0;
}
```

---

### Post by smartbei on 2008-04-08
Ouch!
That was bad...

---

### Post by thebloggu on 2008-04-08
thank you, i solved my problem.

now i am trying to serach for a string in a file using

```
int procura_string_na_bd(char *nick){
	
	char str[100]; //linha
	
	FILE *registos; //declara bd como ficheiro
	
	registos = fopen( "registos.bd", "r" );  // abre ficheiro em bd
	
	if( registos != NULL ){ // se bd != vazio continua
		
		while (fgets(str,sizeof(str),registos)!=NULL){ //lê linha a linha do ficheiro
			
			if (strstr(str,nick)!=NULL) //verifica se uma string existe dentro de outra
				return 1; //verdade
			
		}
		
	}
		
	return 0; //falso

}
```

the problem is that if i search in  "AAAA AB" for B it finds it but it shouldn't. so i have to find string and not amount of characters

---

### Post by mike_g on 2008-04-08
Yes, thats normal behavior for strstr, as it looks for any match within the string. A better way to go about parsing the file may be to split each line using strtok,  go to the column/word position that the password should be at then compare it to your password using strcmp.

---

### Post by thebloggu on 2008-04-08
problem is i don't know how to use strtok. searched for informations but it seems to return only one string while in my case it should retrieve 2.

---

### Post by thebloggu on 2008-04-08
should not this work?

```
int procura(char palavra[10]){

	char linha[100];

	char nome[10],pass[10];

	FILE *bd;

	bd = fopen("bd.txt","r");

	if(bd!=NULL){

		fgets(linha,sizeof(linha),bd);

		sscanf(linha,"%s,%s\n",nome,pass);

		if(strcmp(nome,palavra)==1)
			return 1;

		else return 0;

	}

	return 0;
}
```

it returns segmentation fail

---

### Post by mike_g on 2008-04-09
The problem with sscanf is that you need spaces to delimit your strings for example, say theline in your file is:
```
myuserame,mypassword
```
And you try parse it like you are doing:
```
sscanf(linha,"%s,%s\n",nome,pass);
```
The first %s wont know where to stop reading as the ',' would be counted as par of the string. Another disadvantage to this is that your names and passwords cant have spaces in them. You should be able to get it to work by adding some spaces IE:
```
username , password
```
```
sscanf(linha,"%s %*c %s\n", nome, pass); 
```
but tbh I reckon you would be best off learning how to use strtok, as you can set your own delimeters with it.

---

### Post by thebloggu on 2008-04-09
got it to work, now the problem is that i have my file in

> name,pass

this format. but still, for example i look for 'anana' it says it is there even thoug it is 'banana'.

---

### Post by mike_g on 2008-04-09
How did you get it to work? Are you still using strstr? strcmp won't return 0 comparing two strings that don't match.

If you're bent on using strstr on your file I guess you could get it to work something like:
```
char temp_str[100];
strcpy(temp_str, ",");    
strcat(temp_str, password_entered);
strcat(temp_str, "\n");
if(strstr(temp_str, password_file_line))
    password is good

```
But its pretty ugly, and will break with the slightest inconsistency in your password file.

---

### Post by thebloggu on 2008-04-09
well i reworked my code and it is something like

```
char clean_nl(char compara[50]){

	int a;
	
	a = strlen(compara);

	if(compara[a]=='\n')
		strncpy(compara,compara,a-1);

	printf("%s",compara);

	return compara[50];

}


int procura(char palavra[50],FILE *ficheiro,char *delimit){

	char linha[100];

	char *token = NULL;

	char compara[50];

	printf("1\n");

	if(ficheiro==NULL){

		printf("Erro de leitura, tente novamente\n");

		return 0;

	}

	else{

		printf("2\n");

		while(fgets(linha,sizeof(linha),ficheiro)!=NULL){

			printf("3\n");

			token = strtok(linha,delimit);

			while(token!=NULL){//enquanto houver qualquer no token

				clean_nl(compara);

				printf("4\n");

				printf("%s\n",token);

				sprintf(compara,"%s",token);

				printf("%s\n",palavra);

				printf("%s\n",compara);

				if(strcmp(compara,palavra) == 1 && strlen(compara) == strlen(palavra))
					return 1;

				token = strtok(NULL,delimit);

			}

			return 0;

		}

	}

	return 0;

}



int main(){

	char *palavra;

	FILE *ficheiro;

	char *delimit;

	int a;

	delimit = ",";

	palavra = "ola";

	ficheiro = fopen("ficheiro.a","r");

	a = procura(palavra,ficheiro,delimit);

	if(a==1)
		printf("existe\n");

	else printf("nao existe\n");

	return 0;

}
```

but it is not working, almost. btw how do i return a string in clean_nl?

---

