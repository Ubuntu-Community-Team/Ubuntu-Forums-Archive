---
title: "File handling in c"
date: 2010-04-04
forum: Programming Talk
---

### Post by utkarshjadhav on 2010-04-04
I want to write an array into a file.
So I have opened it in binary mode.
The programs works well for one time of execution.i.e. it writes into file.makes necessary changes we want to .
FOr the next execution I want to retrieve that array from the file.so that I can work on the previous values n modify that.
PLZ F1111!!!!!!!!!!!!

---

### Post by ibuclaw on 2010-04-04
Moved to PT.

How are you saving the array to a file (source?).

---

### Post by utkarshjadhav on 2010-04-04
void intiinthefile(); 
void makeitone(int ,int); 
void makeitzero(int ,int); 
void giv_value_arr(); 
 
void intiinthefile()//*****INITIALIZE TO ZERO IF FILE IS NULL BY CHECKING if(fa==null) 
{ 
    int p,q; 
    fa=fopen("array.txt","w+b"); 
    rewind(fp); 
 
    for(p=0;p<2;p++) 
    { 
        for(q=1;q<=20;q++) 
        { 
            prio[p][q]=0; 
            fprintf(fa,"%d",prio[p][q]); 
        } 
    } 
   //    fwrite(prio,sizeof(int),40,fa); 
    fclose(fa); 
} 
 
void makeitone(int i,int j)//WHENEEVER WE WANT TO MAKE THE NODE VISITED MAKE IT ONE 
{ 
 
    int p,q; 
    prio[i][j]=1; 
    //c=20*i+j; 
    fa=fopen("array.txt","w+b"); 
    rewind(fa); 
    //for(t=0;t<c;t++) 
      //    fseek(fa,1,1);   */ 
    for(p=0;p<2;p++) 
    { 
        for(q=1;q<=20;q++) 
      { 
            fprintf(fa,"%d",prio[p][q]); 
        } 
    } 
    //fwrite(prio,sizeof(int),40,fa); 
 
    fclose(fa); 
} 
void makeitzero(int i,int j)//WHEN EVER WE WANT TO MAKE NODE ZERO MAKE IT ZERO 
{ 
    int t,p,q; 
    //c=(20*i)+j; 
    fa=fopen("array.txt","w+b"); 
   rewind(fa); 
    prio[i][j]=0; 
    for(p=0;p<2;p++) 
    { 
        for(q=1;q<=20;q++) 
        { 
            fprintf(fa,"%d",prio[p][q]); 
        } 
    } 
   //    fwrite(prio,sizeof(int),40,fa); 
 
    fclose(fa); 
} 
void giv_value_arr()//IF FILE ISNT NULL READ FROM FILE AND PUT IT INTO ARRAY 
{ 
 
  int i=0,j=1,t=0,count=0,c; 
    char ch; 
    fa=fopen("array.txt","w+b"); 
    rewind(fa); 
    //fread(fa,"%d",prio[2][21]); 
    while(t<=40) 
    { 
        //fseek(fa,1,SEEK_CUR); 
        fscanf(&c,sizeof(int),1,fa); 
 
        t++; 
        prio[i][j]=c; 
        if(j==20) 
        {   count++; 
            if(count==2) 
            { 
                break; 
            } 
            i++; 
            j=1; 
        } 
        j++; 
 
    } 
 
  } 
    /*for(i=0;i<2;i++) 
    { 
    for(j=1;j<=20;j++) 
    { 
 
    printf("%d",prio[i][j]); 
    } 
    } */ 













PLZ HELP!!!
THE KEY PART IN MY PROJECT ISNT WORKING!!
HELP!!!

---

### Post by Zugzwang on 2010-04-04
> **utkarshjadhav said:**
> 
PLZ HELP!!!
THE KEY PART IN MY PROJECT ISNT WORKING!!
HELP!!!

[LIST=1]
[*]First of all, please surround your code in code-tags or php-tags. Without proper intendation, your code is very hard to read.
[*]Second, when opening a file for reading, "w+b" is probably not the way you want to open it. What about using "rb" instead? Does this help?
[*]Finally, read the man pages for the functions "fscanf","freadf","fread", "fwrite", and "fprintf". By carefully reading, you should get the idea what is going wrong here.
[/LIST]

---

### Post by dwhitney67 on 2010-04-04
+1 on all points.

The OP probably wants something like the following to read in the data:
```

fread(&c, sizeof(c), 1, fa);

```
The OP should also explain why he is starting his secondary array index at 1, and not zero.  From code snip provided, I can only assume the array 'prio' is declared somewhere as:
```

// global variable (bad!!!)
//
int prio[2][21];

...

```

---

