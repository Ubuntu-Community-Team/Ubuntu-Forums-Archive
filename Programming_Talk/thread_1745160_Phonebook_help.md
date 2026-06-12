---
title: "Phonebook help"
date: 2011-04-30
forum: Programming Talk
---

### Post by Anubis.F on 2011-04-30
Greetings everyone!
I'm creating a phone book with lots of functions, and having problems with a few of them.
How do I make a text file, ie, write this data to a text file where each contact is on the same line?
Ok here is my code so far;
  Code:
 ```

#include "ok.h"
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
ADDRESS *hol= NULL; /* Head of our linked list of addresses - 
                        global variable*/

int main()
{
    char input[MAXLEN];   /* Input from the user */
    /*  while (hol != NULL){*/
        FILE *in_file;
        in_file = fopen("address.txt", "w" );
    ;
    /* }*/

    while (1){
        printf ("Add\n Edit\n Delete\n Delete all(Q)\n/  (P)Search for a contact\n/(L)ist\n/(O)Print TABLE\n");
        fgets (input, MAXLEN,stdin);
        switch (input[0]) {
            case ('a'):
            case ('A'):
                add_to_list();
                break;
            case ('d'):
            case ('D'):
                delete_from_list();
                break;

        case ('e'):
           case ('E'):
          modifica();
          break;


        case ('o'):
           case ('O'):
          table_names();
          break;
         
            case ('p'):
            case ('P'):
                print_name();
                break;
            case ('l'):
            case ('L'):
                list_names();
                break;
            case ('x'):
            case ('X'):
                break;
            case ('q'):
            case ('Q'):
                free_list();
                return (0);
            default:
                printf ("Unknown command\n"); 
        }
    
    }
    return 0;    
}
void add_to_list (void) 
/* Add a new name to our address book */
{
    ADDRESS *new_name;
    FILE *outfile;
    new_name= (ADDRESS *)malloc (sizeof (ADDRESS));
    if (new_name == NULL) {
        printf ("Out of memory!\n");
        exit (-1);
       
    }
   outfile = fopen ("contactlist.dat", "w");
    /* Get input for the new item */
   printf ("Enter the position of the contact [numerically/alphabetically]: ");
    fgets (new_name->pos, MAXLEN, stdin);
    printf ("Enter the First Name: ");
    fgets (new_name->name, MAXLEN, stdin);
    printf ("Enter the Last Name: ");
    fgets (new_name->lname, MAXLEN, stdin);
    /* printf ("Enter the Address: ");
    fgets (new_name->address, MAXLEN, stdin);
    printf ("Enter the Telephone number [can contain letters]: ");
    fgets (new_name->phone, MAXLEN, stdin);
    printf ("Enter the Mobile number [can contain letters]: ");
    fgets (new_name->mobile, MAXLEN, stdin);*/
    /* Chain the new item into the list */
    new_name->next= hol;
    hol= new_name;
}    

void delete_from_list (void)
/* Remove a name from the address book */
{
    ADDRESS *del_ptr;   /* Pointer to find name to delete */
    ADDRESS *prev_ptr;  /* Pointer to name BEFORE this name */
    char del_name[MAXLEN]; /* Name to delete */
    
    printf ("Name> ");
    fgets (del_name, MAXLEN, stdin);
    /* The first item in the list being deleted is a special case */
    if (hol == NULL) {
        printf ("No list to delete from\n");
        return;
    }
    /* If the first name is the correct one then move the head of list on to the next head of list */
    if (strcmp(hol->name, del_name) == 0) {
        del_ptr= hol;
        hol= hol->next;
        free(del_ptr);
        return; 
    }
    /* Otherwise loop round the list looking for the name */
    prev_ptr= hol;
    while (prev_ptr->next != NULL) {
        /* We've found the name so delete it */
        if (strcmp(prev_ptr->next->name,del_name) == 0) {
            del_ptr= prev_ptr->next;
            prev_ptr->next= del_ptr->next;
            free(del_ptr);
            return;
        }
        prev_ptr= prev_ptr->next;
    }
    printf ("Name not found!\n");
}

void print_name (void)
/* Print a name from the list */
{
    char name[MAXLEN];  /* Name to look for */
    ADDRESS *search_ptr; /* Pointer to search list for name */
    printf ("Name> ");
    fgets (name, MAXLEN, stdin);
    search_ptr= hol;
    while (search_ptr != NULL) {
        if (strcmp (search_ptr->name, name) == 0) {
            printf ("Position in the Phone Book: %s", search_ptr->pos);
            printf ("Last Name: %s", search_ptr->lname);
            printf ("Address: %s", search_ptr->address);
            printf ("Telephone : %s", search_ptr->phone);
            printf ("Mobile : %s", search_ptr->mobile);
            return;
        }
        search_ptr= search_ptr->next; /* Move to next item */
    }
    printf ("No such name\n");
}


void list_names (void)
/* List all names in the book */
{
    ADDRESS *tmp_ptr; /* Traverses list */
    printf ("All names in address book:\n");
    tmp_ptr= hol;
    while (tmp_ptr != NULL) {
      printf ("%s %s",tmp_ptr->name,tmp_ptr->lname);
        tmp_ptr= tmp_ptr->next;
    }
}


void free_list (void)
/* Free memory for list */
{
    ADDRESS *del_ptr;  /* Pointer to part to delete */
    
    while (hol != NULL) {
       del_ptr= hol;  /* Store the head of list */
       hol= hol->next; /* Move on to the next bit */
       free(del_ptr);  /* Free the memory for the bit we just left */
    }
}


void table_names (void)
{
    ADDRESS *tmp_ptr;
    printf ("All names in address book:\n");
    tmp_ptr= hol; 
      printf(" ______________________________\n");
      printf("|  FIRST NAMES   | LAST NAMES  |\n");
      printf("|________________|_____________|\n");
    while(tmp_ptr!=NULL)
{   
  printf ("%s%s",tmp_ptr->name,tmp_ptr->lname);
        tmp_ptr= tmp_ptr->next;
}
    }

void modifica(void)
{
char scegli;
 ADDRESS*ptr;
  char str1[MAXLEN];
  ptr=hol;
if(!ptr)
    printf("\nPhonebook empty!!");
else
    {
   printf("\nInsert last name: ");
   scanf("%s", str1);
   if(strcmp(str1, ptr->lname)!=0)
     {
     /*     ptr=ptr->link_dx;
        if(ptr==NULL)*/
       printf("\nContat nonexistent!");}
   else{
      printf("\nContact: %s %s\n", ptr->lname, ptr->name);
      printf("\nChange the last name too? (y/n) ");
      scanf("%1s", &scegli);
   }
      if(scegli=='y')
          {
         printf("\nInsert new last name: ");
         scanf("%s", str1);
         strcpy(ptr->lname, str1);
         }
      printf("\nChange the name??(y/n) ");
      scanf("%1s", &scegli);
      if(scegli=='y')
          {
         printf("\nInsert new name: ");
         scanf("%s", str1);
         strcpy(ptr->name, str1);
         }
      /*      printf("\nModify the number?(y/n) ");
      scanf("%1s", &scegli);
      if(scegli!='n')
          {
         printf("\nInsert new number: ");
         scanf("%s", str1);
         strcpy(ptr->numero, str1);
         }*/
    }
 printf("DONE!");

```} 
Thanks in advance.

---

### Post by cgroza on 2011-05-01
```
 yourfile << name << phone << address << endl;
```

---

