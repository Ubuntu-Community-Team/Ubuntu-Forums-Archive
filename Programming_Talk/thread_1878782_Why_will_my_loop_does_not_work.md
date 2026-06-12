---
title: "Why will my loop does not work"
date: 2011-11-10
forum: Programming Talk
---

### Post by atoivan on 2011-11-10
why is the loops not working ?
 
i am using an Indefinite for loop >  for( (;;)) 
 but  it does not stop looping so i tried to use while loop and with the while loop when > (bra>2)
it still print[quote] ("do u want to add more y or n")/quote]which i do not want it to do so.
and when ( bra ==1) it does not allow me to enter Y or N option it skips the scanf() do u have any idea why it does that.
and what is the correct thing to do pls

with the for loop dis is the code 
```
#include <stdio.h>
#include <stdlib.h>
#include <ctype.h>
#include <string.h>

void create_new_stock(void);
void display_stock(void);
void sales(void);
void modify(void);
void Additem(void);
void Viewitems(void);
void Viewcategory(void); 
void Editcategory(void);
void Edititems(void);
void Edit(void);
void Deleteitem(void);
void Deletecategory(void);
void PrintBeeper(void);
void CreateFile(void);
void DeleteFile(void);
void sel();
 

 
double     u_prx = 0.0;             
double     total=0.0;                 
double     G_total=0.0;             
double     amut_b=0.0;             
double     amut_u=0.0;                
double     S_prx_Blk=0.0;            
double     S_prx_u=0.0;            
double     T_amut_blk=0.0;            
double    T_amut_u =0.0;            
double  qty_sold = 0.0;            
int     T_qty_bulk =0;            
int     T_qty_u =0;            
int     G_T_qty_bulk=0;            
int        G_T_qty_u=0;            
int           qty_u= 0;                 
int        qty_left = 0;             
int        qty_bulk = 0;             
 
char cate[20];                
char iname[20];                 
char code[6];                     
 

 
void create_new_stock()
{
    int bra;
    char ans;
printf("Enter Category ");
scanf("%s",cate);
 
printf("How many brands do u want to add?");
scanf("%d",&bra);
for(;;)
{
 
printf("Enter brand name");
scanf("%s",iname);
 
printf("Enter Buying price(bulk)");
scanf("%lf",&amut_b);
 
puts("Enter Quantity in bulk");
scanf("%d",&qty_bulk);
 
puts("Enter Quantity of items (number of items in a box)");
scanf("%d",&qty_u);
 
T_qty_u=qty_bulk*qty_u;
T_amut_blk=amut_b/qty_u;
 
puts("Enter Selling price for(box)");
scanf("%lf",&S_prx_Blk);
 
puts("Enter selling price for unit");
scanf("%lf",&S_prx_u);
 
if (bra<=1)
 
puts("do u want to add more y or n");
scanf("%c",&ans);
 
if(tolower(ans) == 'n')             
break;
 
}
getchar();
}
 

void display_stock()
{
 
    
}
 
void sales()
{
 
    
    }
 
void modify()
{
 
    
 
}
 
int main()
{
char sele; // seletion of data

puts(" Welcome to my sales Program");
puts("<1> \t Create a new stock ");
puts("<2> \t Display Stock");
puts("<3> \t Sales");
puts("<4> \t Modify");
puts("<5> \t exit");
 
puts("Enter selection");
scanf("%c",&sele);
 

switch (sele)
{
case '1':
create_new_stock();
break;
case '2':
display_stock();
break;
case '3':
sales();
break;
case '4':
modify();
break;
case '5':
exit(1);
break;
 
    }
return 0;
getchar();
        }
```

with the while loop this is the code

```
#include <stdlib.h>
#include <ctype.h>
#include <string.h>
#include  <ncurses.h>
 
void create_new_stock(void);
void display_stock(void);
void sales(void);
void modify(void);
void Additem(void);
void Viewitems(void);
void Viewcategory(void);
void Editcategory(void);
void Edititems(void);
void Edit(void);
void Deleteitem(void);
void Deletecategory(void);
void PrintBeeper(void);
void CreateFile(void);
void DeleteFile(void);
void sel();
 

 
double  u_prx = 0.0;
double  total=0.0;
double  G_total=0.0;
double  amut_b=0.0;
double  amut_u=0.0;
double  S_prx_Blk=0.0;
double  S_prx_u=0.0;
double  T_amut_blk=0.0;
double  T_amut_u =0.0;
double  qty_sold = 0.0;
int     T_qty_bulk =0;
int     T_qty_u =0;
int     G_T_qty_bulk=0;
int     G_T_qty_u=0;
int     qty_u= 0;
int     qty_left = 0;
int     qty_bulk = 0;
 
char cate[20];
char iname[20];
char code[6];
<pre>
void create_new_stock()
{
    int bra;
    char ans;
int a=1;
printf("Enter Category \n");
scanf("%s",cate);
printf("How many brands do u want to add?\n");
scanf("%d",&bra);
while(a <= bra)
{
printf("Enter brand name\n");
scanf("%s",iname);
printf("Enter Buying price(bulk)\n");
scanf("%lf",&amut_b);
printf("Enter Quantity in bulk\n");
scanf("%d",&qty_bulk);
printf("Enter Quantity of items (number of items in a box)\n");
scanf("%d",&qty_u);
T_qty_u=qty_bulk*qty_u;
T_amut_blk=amut_b/qty_u;
printf("Enter Selling price for(box)\n");
scanf("%lf",&S_prx_Blk);
puts("Enter selling price for unit");
scanf("%lf",&S_prx_u);
a++;
puts("do u want to add more y or n");
scanf("%c",&ans);
if(tolower(ans) =='Y')             
break;
}
 
}
 
void display_stock()
{
 
    
}
 
void sales()
{
 
    
    }
 
void modify()
{
 
    
 
}
 
int main()
{
char sele; // seletion of data

puts(" Welcome to my sales Program");
puts("<1> \t Create a new stock ");
puts("<2> \t Display Stock");
puts("<3> \t Sales");
puts("<4> \t Modify");
puts("<5> \t exit");
 
puts("Enter selection");
scanf("%c",&sele);
 

switch (sele)
{
case '1':
create_new_stock();
break;
case '2':
display_stock();
break;
case '3':
sales();
break;
case '4':
modify();
break;
case '5':
exit(1);
break;
 
    }
return 0;
getchar();
        }
```

---

### Post by karlson on 2011-11-10
> **atoivan said:**
> why is the loops not working ?

[yada yada yada yada yada deleted]



In first code: use curly braces to distinguish then and else clause of the if statement.  

In the second code do the same but also when you are comparing:
```

tolower(<char>) == 'Y'

```
Do you ever expect it to be true?

---

