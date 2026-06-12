---
title: "problem in embedding a tic tac toe game in a client server program made in c"
date: 2011-06-15
forum: Programming Talk
---

### Post by rags_asr on 2011-06-15
hii,
i am new to the forum,but in urgent need of help
i developed a client server program and a tic tac toe game using c
i am facing a problem in embedding my game in the client server program so that the game can be played by multiple clients(2 in dis case)
any help would b really appreciated nd would b very helpful
> 
my server program is


#include <stdio.h>
#include <stdlib.h>
#include <sys/types.h>
#include <sys/socket.h>
#include <netinet/in.h>
#include <arpa/inet.h>
#include <unistd.h>
#include <sys/un.h>
#define SERV_PORT 34445

void process(int sockfd);

int main(int argc,char **argv)
{
 printf("This is the server program\n");
//naming variables
 int server_sockfd, client_sockfd;
pid_t childpid;
int server_len, client_len;
struct sockaddr_in  server_address;
struct sockaddr_in  client_address;

int result;
int res;
int rc;

// removing old sockets
unlink("server_socket");
server_sockfd=socket(AF_INET,SOCK_STREAM,0);
if (server_sockfd == -1) { 
		perror("Socket create failed.\n") ; 
		return -1 ; 
	} 
//naming of socket
server_address.sin_family = AF_INET;
	server_address.sin_addr.s_addr = inet_addr("192.155.0.23");
	server_address.sin_port = htons(SERV_PORT);
	server_len = sizeof(server_address);

	result = bind(server_sockfd, (struct sockaddr *)&server_address,server_len);
	if(result == -1)
	{
		perror("Error has occurred");
		exit(-1);
	}
res=listen(server_sockfd, 5);
if(res==-1)
{
perror("error");
exit(-1);
}
for ( ; ; ) 
{
		client_len = sizeof(client_address);
		client_sockfd = accept(server_sockfd, (struct sockaddr *) &client_address, &client_len);

		if ( (childpid = fork()) == 0) {	/* child process */
			close(server_sockfd);	
			process(client_sockfd);	/* process the request */
			exit(0);
		}
		close(client_sockfd);			/* parent closes connected socket */
	}
}

void process(int sockfd)
{


        ssize_t n;
        char buffer1[80], buffer2[80];


        for ( ; ; ) {

                if ( (n = recv(sockfd, buffer1, sizeof(buffer1),0)) == 0)
                        return;         /* connection closed by other end */
		printf ("Client says: %s", buffer1);
gets(buffer2);
                send(sockfd, buffer2, sizeof(buffer2),0);
        }

}

> 

my client program is


#include <stdio.h>
#include <stdlib.h>
#include <sys/types.h>
#include <sys/socket.h>
#include <netinet/in.h>
#include <arpa/inet.h>
#include <unistd.h>
#include<string.h>


#define SERV_PORT 34445
#define MAXLINE 80

///   CLIENT   

void process(FILE *FP, int sockfd);
int main(int argc, char *argv[])
{
	printf("This is the client program\n");

	int sockfd;
	int len, rc ;
int result;
	struct sockaddr_in address;
      
  

   //Create socket for client.
	sockfd = socket(AF_INET, SOCK_STREAM, 0);
	if (sockfd == -1) { 
		perror("Socket create failed.\n") ; 
		return -1 ; 
	}
	
	//Name the socket as agreed with server.
	address.sin_family = AF_INET;
	address.sin_addr.s_addr = inet_addr("192.155.70.24");
	address.sin_port = htons(SERV_PORT);
	len = sizeof(address);

	result = connect(sockfd, (struct sockaddr *)&address, len);
	if(result == -1)
	{
		perror("Error has occurred");
		exit(-1);
	}

	process(stdin, sockfd);	
		exit(0);
}
void process(FILE *fp, int sockfd)
{
        char   sendline[MAXLINE];
        char   string1[MAXLINE], string2[MAXLINE];

        while (fgets(sendline, MAXLINE, fp) != NULL) {
                   
                write(sockfd, sendline, sizeof(sendline));

                if (read(sockfd, string2, sizeof(string2)) == 0) {
                        printf("Client: server terminated prematurely");
			exit (0);
		}

                printf("Server says: %s\n", string2);


        }
}


> 

and my tic tac toe game is




#include<stdio.h>




int Board();
int PlayerX();
int PlayerO();
int Player_win();
int check();
int win=0,wrong_X=0,wrong_O=0,chk=0;

char name_X[30];
char name_O[30];
int pos_for_X[3][3];
int pos_for_O[3][3];
int pos_marked[3][3];

int main()
{
	
	int i,ch,j;
	char ans;

	do
	{
		
		printf("\n\t\t\t\tTIC TAC TOE");
		printf("\n\t\t\t\t");
		printf("\n1.Start The Game");
		printf("\n2.Quit The Game");
		printf("\nEnter your choice(1-2) : ");
		scanf("%d",&ch);
		switch(ch)
		{
			case 1:
				chk=0;
				win=0;
				for(i=1;i<=3;i++)
				{
					for(j=1;j<=3;j++)
					{
						pos_for_X[i][j]=0;
						pos_for_O[i][j]=0;
						pos_marked[i][j]=0;
					}
				}
				printf("\n\n");
				printf("\nEnter the name of the player playing for \'X\': ");

				
			        scanf("%s",&name_X);
				printf("\nEnter the name of the player playing for \'O\': ");
				scanf("%s",&name_O);
				Board();
				for(;;)
				{
					if(win==1)
						break;
					check();
					if(chk==9)
					{
						printf("\n\t\t\tMATCH DRAWS!!");
						printf("\nPress any key....");
						break;
					}
					else
						chk=0;
					printf("\nTURN FOR %s:",name_X);
					PlayerX();
					do
					{
						if(wrong_X!=1)
							break;
						wrong_X=0;
						printf("\nTURN FOR %s:",name_X);
						PlayerX();
					}while(wrong_X==1);
					check();
					if(chk==9)
					{
						printf("\n\t\t\tMATCH DRAWS");
						printf("\nPress any key....");
						break;
					}
					else
						chk=0;
					printf("\nTURN FOR %s:",name_O);
					PlayerO();
					do
					{
						if(wrong_O!=1)
							break;
						wrong_O=0;
						printf("\nTURN FOR %s:",name_O);
						PlayerO();
					}while(wrong_O==1);

					}
				Board();
				if(win!=1)
				{
					printf("\n\t\t\tMATCH DRAWS!!");
					printf("\nPress any key.......");
				}
				
				break;
			case 2:
				printf("\n\n\n\t\t\tThank You For Playing The Game.");
				

			      break;
		}
		printf("\ndo you want to continue(Y/N)? ");
		scanf(" .

%c",&ans);
		}while(ans=='Y'  || ans=='y');
	
}


int Board()
{
	int i,j;
	printf("\n\t\t\t\tTIC TAC TOE BOARD");
	printf("\n\n\n");
	printf("\n\t\t\t    1\t      2\t        3");
	for(i=1;i<=3;i++)
	{
		printf("\n \t\t\t _____________________________");
		printf("\n \t\t\t||\t  ||\t   ||\t     ||");
		printf("\n\t\t%d\t",i);
		for(j=1;j<=3;j++)
		{

			if(pos_for_X[i][j]==1)
			{
				printf("    X");
				printf("     ");
			}
			else if(pos_for_O[i][j]==1)
			{
				printf("    O");
				printf("     ");
			}
			else
			{
				printf("          ");
				continue;
			}
		}
		printf("\n\t\t\t||\t  ||\t   ||\t     ||");
	}
	printf("\n\t\t\t________________________________");
	Player_win();
	return(0);
}


int PlayerX()
{
	int row,col;
	if(win==1)
		return;
	printf("\nEnter the row no. : ");
	scanf("%d",&row);
	printf("Enter the column no. : ");
	scanf("%d",&col);
	if(pos_marked[row][col]==1 || row<1 || row>3 || col<1 || col>3)
	{
		printf("\nWRONG POSITION!! Press any key.....");
		wrong_X=1;
		Board();
	}
	else
	{
		pos_for_X[row][col]=1;
		pos_marked[row][col]=1;
		Board();
	}
	return(0);
}
int PlayerO()
{
	int row,col;
	if(win==1)
		return;
	printf("\nEnter the row no. : ");
	scanf("%d",&row);
	printf("Enter the column no. : ");
	scanf("%d",&col);
	if(pos_marked[row][col]==1 || row<1 || row>3 || col<1 || col>3)
	{
		printf("\nWRONG POSITION!! Press any key....");
		wrong_O=1;
		Board();
	}
	else
	{
		pos_for_O[row][col]=1;
		pos_marked[row][col]=1;
		Board();
	}
	return(0);
}
int Player_win()
{
	int i;
	for(i=1;i<=3;i++)
	{
		if(pos_for_X[i][1]==1 && pos_for_X[i][2]==1 && pos_for_X[i][3]==1)
		{
			win=1;
			printf("\n\nRESULT: %s wins!!",name_X);
			printf("\nPress any key............");
			return;
		}
	}
	for(i=1;i<=3;i++)
	{
		if(pos_for_X[1][i]==1 && pos_for_X[2][i]==1 && pos_for_X[3][i]==1)
		{
			win=1;
			printf("\n\nRESULT: %s wins!!",name_X);
			printf("\nPress any key............");
			return;
		}
	}
	if(pos_for_X[1][1]==1 && pos_for_X[2][2]==1 && pos_for_X[3][3]==1)
	{
		win=1;
		printf("\n\nRESULTL: %s wins!!",name_X);
		printf("\nPress any key......");
		return;
	}
	else if(pos_for_X[1][3]==1 && pos_for_X[2][2]==1 && 
pos_for_X[3][1]==1)
	{
        	win=1;
		printf("\n\nRESULT: %s wins!!",name_X);
                printf("\nPress any key.....");
		return;
	}

        for(i=1;i<=3;i++)
	{
		if(pos_for_O[i][1]==1 && pos_for_O[i][2]==1 && pos_for_O[i][3]==1)
		{
			win=1;
			printf("\n\nRESULT: %s wins!!",name_O);
                        printf("\nPress any key.....");
			return;
		}
	}
	for(i=1;i<=3;i++)
	{
		if(pos_for_O[1][i]==1 && pos_for_O[2][i]==1 && pos_for_O[3][i]==1)
		{
			win=1;
			printf("\n\nRESULT: %s wins!!",name_O);
                        printf("\nPress any key.....");
			return;
		}
	}
	if(pos_for_O[1][1]==1 && pos_for_O[2][2]==1 && pos_for_O[3][3]==1)
	{
		win=1;
		printf("\n\nRESULT: %s wins!!",name_O);
		printf("\nPress any key.....");
		return;
	}
	else if(pos_for_O[1][3]==1 && pos_for_O[2][2]==1 && 
pos_for_O[3][1]==1)
	{
        	win=1;
		printf("\n\nRESULT: %s wins!!",name_O);
		printf("\nPress any key.....");
		return;
	}
	return(0);
}
int check()
{
	int i,j;
	for(i=1;i<=3;i++)
	{
		for(j=1;j<=3;j++)
		{
			if(pos_marked[i][j]==1)
				chk++;
			else
				continue;
		}
	}



plzzz suggest asap
thank u
	return(0);
}



---

### Post by Tony Flury on 2011-06-15
Suggestions : 
1) Post your code in CODE tags - so people can scroll through it - it should also properly preserve any formatting
2) State clearly what the problems are - compiler errors, functional errors ? We will try to help if we know what the problems are, if will be very unlikely that someone will compile your code and run it and try to figure out why the problems are all on their own.
3) If you need an answer ASAP - maybe explain why - Tic-tac-toe does not sound like a life critical (or even business critical) problem.

---

### Post by Petrolea on 2011-06-15
You need to send data about which parts of 2D array have already been marked with either X or O.

---

### Post by rags_asr on 2011-06-19
1)i hav actually written a problem in the forum for the first time,so 4m next time onwards i will keep my programs in the code,nd keep your suggestions in mind.

2)no compiler or functional error are coming,the basic problem is ,i am not able to figure out the way  2 make this game played by 2 differnt users at the same time,
i need help in figuring out the neccesary changes that are required to be done in the client and server program ,so that the game can be played by 2 users simultaneously.i guess i need to use file handling to read the inputs from the player and store them write them so the other player can see the move of player 1 and so on,but i dont know how to use it.

3)and its urgent because its a college project and the submission date is near
thank u

---

### Post by rags_asr on 2011-06-19
yaa but how do i do that??

---

### Post by Petrolea on 2011-06-19
> **rags_asr said:**
> yaa but how do i do that??

You expect us to write it for you? We're here to help, not to do your college projects. If you come up with something and it won't work as expected, we can help you fix it. But not just write the whole program for you.

---

### Post by rags_asr on 2011-06-19
no i dnt expect you to write the program for me...i am asking for your help in letting me know the concept or the logic.like what should b my next step.

---

### Post by Petrolea on 2011-06-19
> **rags_asr said:**
> no i dnt expect you to write the program for me...i am asking for your help in letting me know the concept or the logic.like what should b my next step.

[B]Logic would be like this:
[/B]
Make a program that will wait for incoming data, which will be the position marked by either X or O.

When program accepts data, it marks it on screen. Remember that both players must always see the same.

[B]The data exchange part:
[/B]
You can make one player server and the other one client, or make them both clients that will connect to a server and save/read data from there.

There are probably more ways of doing this that I'm unaware of, but I think this will fit your needs.

---

