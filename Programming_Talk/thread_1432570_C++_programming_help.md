---
title: "C++ programming help"
date: 2010-03-17
forum: Programming Talk
---

### Post by jjones237 on 2010-03-17
Help with food bank program.  When running this program it should reprompt for the menu after fufilling a request or adding a donation but it loops through the choice instead of going back through the menu.  here's the code, what should i do?  Any help appreciated.





#include <stdio.h>
#include <stdlib.h>
#include <string.h>

int main() {
    
    int choice;
    char word[20];
    char donation_inv_type[100][20];
    int donation_amount[100];
    char request_inv_type[100][20];
    int request_amount[100];
    int m;
    int i;
    int j;
    int ReqC=0;
    int DonC=0; 
    int SAVEI;

    // set all arrays to 0.
    for (i=0; i<100; i++){ 
     for (j=0; j<20; j++){
       donation_inv_type[i][j] = 0;
       request_inv_type[i][j] = 0; }}
       
    for (i=0; i<100; i++) {
     donation_amount[i] = 0;
     request_amount[i] = 0;}
   
   


    // Print the menu and read in the user's choice.    
    printf("Welcome to the Food Bank\n\n");
    printf("1.Enter a Donation\n2.Enter a Request\n3.Fulfill the earliest Request\n4.Print Status Report\n5.Exit\n\n");
    printf("Enter your choice:\n\n");
    scanf("%d", &choice);
    
    // Keep on going until the user quits.
    while (choice != 5) {
          
          // Entering the Donation
          if (choice == 1) {  
                     
    char word[20];
    int m;
    char donation_inv_type[100][20];
    int donation_amount[100];              
    int DonC=0;
    int SAVEI;
    int i;   
      
                      
                               
             printf("Enter Inventory Type:\n");
             scanf("%s", word);
             printf("Enter the Amount:\n");
             scanf("%d", &m);
             printf("\n");
             printf("Donation Added!\n");
             
                          
            if (DonC == 0) {
              strcpy(donation_inv_type[0], word);
              donation_amount[0] = m;
              DonC++ ;}
                  
                        
             
            else if (DonC>0){ 
                SAVEI = -1; 
                for (i=0; i<DonC; i++){
                  if ((strcmp(donation_inv_type[i], word)) == 0){
                    SAVEI = i; }
                  if (SAVEI > -1){
                    donation_amount[SAVEI]+= m;}
                  else {
                    strcpy(donation_inv_type[DonC], word);   
                    donation_amount[DonC] = m; 
                    DonC++;}
                    }}        
                         
                         }
              
             
          
          
          // Execute a withdrawal. No error checking done here.
          else if (choice == 2) {
               
    char word[20];
    int m;
    char request_inv_type[100][20];
    int request_amount[100];              
    int ReqC=0;           
               
            printf("Enter Inventory Type:\n");
             scanf("%s", word);
             printf("Enter the Amount:\n");
             scanf("%d", &m);
             printf("\n");
             printf("Request Added!\n");
            
             if (ReqC == 0){
              strcpy(request_inv_type[0], word);
              request_amount[0] = m;
              ReqC++ ;
                  }    
             
             else if (ReqC>0){ 
                 strcpy(request_inv_type[ReqC], word);   
                 request_amount[ReqC] = m;  
                 ReqC++; }  
          }
          
          // Prints out the value of balance.
          else if (choice == 3) {
            
    int SAVEI;
    int i;
    int DonC=0;
    char donation_inv_type[100][20];
    int donation_amount[100];
    char request_inv_type[100][20];
    int request_amount[100];
    int ReqC=0;
         
            
            
            
            printf("-------- Fulfilling Requests --------\n\n");
            
            // option 1
            SAVEI = -1;
            for (i=0; i<DonC; i++){
                
                // Search for matching inventory. 
                if (strcmp(donation_inv_type[i], request_inv_type[0]) == 0){
                      SAVEI = i;
                      if (SAVEI != -1){ // If a match is found...
                       
                       
                        // If the amount of donations excedes the amount requested, subtract the requested for the donated.
                        if (donation_amount[i] > request_amount[0]) {
                                 donation_amount[i] = donation_amount[i] - request_amount[0]; 
                                 for(i = SAVEI; i < ReqC; i++){
                                      strcpy(request_inv_type[i], request_inv_type[i+1]);
                                      request_amount[i] = request_amount[i+1]; 
                                      ReqC--;   }
                                 printf("Request Fulfilled!\n\n");     
                                      }
                                      
                          // If the amount requested excedes the amount donated, the order may only be partially fulfilled.
                          else if (request_amount[0] > donation_amount[i]) {
                                 request_amount[0] = request_amount[0] - donation_amount[i];
                                 for (i = SAVEI; i < DonC; i++){
                                     strcpy(donation_inv_type[i], donation_inv_type[i+1]);
                                     donation_amount[i] = donation_amount[i+1]; 
                                     DonC--;    }
                                  printf("Partially Fulfilled!\n\n");  
                                     }
                                 
                         // If amount donated matches the amount requested, both items get taken out of the list. 
                          else if (donation_amount[i] = request_amount[0]) { 
                                  for (i = SAVEI; i < DonC; i++){
                                     strcpy(donation_inv_type[i], donation_inv_type[i+1]);
                                     donation_amount[i] = donation_amount[i+1]; 
                                     DonC--;    }
                                     
                                  for(i = SAVEI; i < ReqC; i++){
                                      strcpy(request_inv_type[i], request_inv_type[i+1]);
                                      request_amount[i] = request_amount[i+1]; 
                                      ReqC--;   }
                                   printf("Request Fulfilled!\n\n");   
                                      }
                                      }// end of the "SAVEI = 1" if statement                                                             
                                      }// end of the "strcmp"
                                      }// end of the "for loop"
                                                                         
                // If the dontation is not found...      
                if (SAVEI = -1) {
                   printf("Cannot be Fulfilled\n\n"); } 
                                      }// end of "choice = 3"                  
          
    
          
          // Print out tables
          else if (choice == 4) {
               
           
               
               
            for (i=0; i<DonC; i++){
                printf("%s  %d\n", donation_inv_type[i], donation_amount[i]);
                } // end for loop                
            for (i=0; i<ReqC; i++){ 
                printf("%s  %d\n", request_inv_type[i], request_amount[i]);
                }} // end for loop and choice 4
             
                    
          // Print out an error message for an invalid choice.
          else if (choice != 5) {
             printf("Sorry that was invalid.\n\n");
             // Print the menu and read in the user's choice.    
             printf("Welcome to the Food Bank\n\n");
             printf("1.Enter a Donation\n2.Enter a Request\n3.Fulfill the earliest Request\n4.Print Status Report\n5.Exit\n\n");
             printf("Enter your choice:\n\n");
             scanf("%d", &choice);
             }// end of choice !=5
             }// end of WHILE loop
             
        
             
    printf("Thank You for running the software. Bye for now.\n");
          
    system("PAUSE");
    return 0;
} // end main

---

### Post by schauerlich on 2010-03-17
1) Is this homework?
2) Please use code tags. Go [here](http://www.challenge-you.com/bbcode) to add syntax hilighting, which will make your code easier to read.
3) You've got one really long main() function. You should consider breaking it up into smaller chunks and calling those functions from within main. Main should contain the overall flow of your program, not every detail of its implementation.

---

### Post by jjones237 on 2010-03-17
It is homework, i did all of this already but I cannot figure out what to change to just make the first two sections, the requests and donations, to return to the main menu.  If you can't help because it is homework i understand but i could really use some pointers.

---

### Post by schauerlich on 2010-03-17
[http://ubuntuforums.org/showthread.php?t=717011](http://ubuntuforums.org/showthread.php?t=717011)

[[img]http://imgs.xkcd.com/comics/pointers.png[/img]](http://xkcd.com/138/)

---

### Post by Some Penguin on 2010-03-18
Do you expect the compiler to read your mind and move code that you put outside the loop, inside it?

---

### Post by Xyro on 2010-03-18
Sure hope you're not supposed to be writing that in C++...

---

### Post by roccivic on 2010-03-18
It's not even C++, it's plain C...

---

### Post by gtr32 on 2010-03-18
Your scanf needs to be inside the loop. Instead of 

```
while()
{...}
```

consider doing:

```
do
{
} while ();
```

Since it's homework, you should figure out the rest.

---

### Post by munky99999 on 2010-03-18
> **schauerlich said:**
> 
3) You've got one really long main() function. You should consider breaking it up into smaller chunks and calling those functions from within main. Main should contain the overall flow of your program, not every detail of its implementation.

Does this usually lead to better performance or is it just a formatting/readability thing?

---

### Post by dwhitney67 on 2010-03-18
> **munky99999 said:**
> Does this usually lead to better performance or is it just a formatting/readability thing?

Are you asking about CPU performance?  Well, then no.

If you are talking about the performance of a handful of people maintaining an application, of say 500K to 1000K lines of code, then, yes it matters.  The performance of the team of workers will be practically nil.

---

### Post by schauerlich on 2010-03-18
> **munky99999 said:**
> Does this usually lead to better performance or is it just a formatting/readability thing?

Readability and maintainability. For any non-trivial program, you're going to have enough lines that putting it all in main is simply unmaintainable.

---

