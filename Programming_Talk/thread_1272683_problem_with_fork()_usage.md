---
title: "problem with fork() usage"
date: 2009-09-22
forum: Programming Talk
---

### Post by Kotsouba on 2009-09-22
i am having real trouble with an assignment i got.
I had to build a 10 level binary tree of processes using the fork() function
each process had to print its level-parentname-1 if its the left child or level-parentname-2 if its the left child. For example the 1st level process should print 1 the second lvl 211 and 212 and the third 32111 32112 32121 32122 e.t.c.Here is what i got till now```

#include <stdio.h>   /* printf, stderr, fprintf */
#include <unistd.h>  /* _exit, fork */
#include <stdlib.h>  /* exit */
#include <errno.h>   /* errno */
#include <string.h>   /* errno */



int main(void)
{
 int i;
 int LeftRightChild=1;
 int level=2;
 int parent=1;
 printf("%d\n",parent);
 child_node(level,parent,LeftRightChild);


return(0);
}

int child_node (level,current_node,LeftRightChild)
{
int pid,nodex;
char Node[768];
char convert[768];
pid=fork();
if (LeftRightChild==1)

{
if (pid == 0)  // im the child
{
 sprintf(convert,"%d",level);
 strcat(Node,convert);
 sprintf(convert,"%d",current_node);
 strcat(Node,convert);
 sprintf(convert,"%d",LeftRightChild );
 strcat(Node,convert);
 printf("%s\n",Node);
 LeftRightChild=LeftRightChild+1;
 child_node(level,current_node,LeftRightChild);// gia to de3i paiditero paidi
}
}

else if (LeftRightChild==2)
{
if (pid == 0) // im the child
{
sprintf(convert,"%d",level);
 strcat(Node,convert);
 sprintf(convert,"%d",current_node);
 strcat(Node,convert);
 sprintf(convert,"%d",LeftRightChild );
 strcat(Node,convert);
 printf("%s\n",Node);
 LeftRightChild=LeftRightChild+1;
 nodex=atoi(Node);
 current_node=nodex;
 child_node(level,current_node,LeftRightChild);// gia to de3i paiditero paidi
}
}
else
{
   
    if (level<3)
    {
    puts("\n ");
    LeftRightChild=1;//gamao
    level=level+1;
    child_node(level,current_node,LeftRightChild);
    }
    else
    {
        
        exit(0);
    }
}
}







```

The problem is that for a 3 level tree it prints 1 211 212 and then makes four child of the 212 process the output is: 1 211 212 32121 32122 32121 32122!
any help Greatly apreaciated!:popcorn:

---

### Post by dwhitney67 on 2009-09-22
Can you please re-specify your program's requirements?  I did not quite understand what you posted in the opening paragraph of your post.  Perhaps what I found confusing is that you used numbers in your examples versus using something to indicate what the numbers meant.

---

### Post by Kotsouba on 2009-09-22
What i need to do is Create a 10 level binary tree of processes.
each process has to print its level- whats its parent process printed and- and 1 if its the left child or 2 if its the right child!
a 2 level tree example would print:

1 //the parent process
211// its left child
212// ots right child

32111
32112
32121
32122


my problem is that witht he current code i get:


1
211
212
32121
32122
32121
32122

so i get four childs at the third level which is correct but i am getting four childs from 1 level 2 process and none from the other!

---

### Post by dwhitney67 on 2009-09-22
The usage of forking and recursion can be daunting.  Are each requisites?

Here's an example that performs recursion, but not the forking; also, I do not know if the output is formatted as you wish.
```

#include <stdio.h>
#include <unistd.h>
#include <stdlib.h>
#include <string.h>

void child_node(int level, const char* curNode);

int main()
{
   printf("1\n\n");

   child_node(2, "1");

   return 0;
}

void child_node(int level, const char* curNode)
{
   char node1[128] = {0};
   char node2[128] = {0};

   if (level <= 3)
   {
      sprintf(node1, "%d%s%d", level, curNode, 1);
      printf("%s\n", node1);


      sprintf(node2, "%d%s%d", level, curNode, 2);
      printf("%s\n", node2);

      printf("\n");

      child_node(++level, node1);
      child_node(level, node2);
   }
}

```

---

### Post by Kotsouba on 2009-09-22
i fixed up my code ur way, but my problem persists the forking part is ok but after level 2 i cant pass the name of the parent process to the new childs,here is my current code```
#include <stdio.h>   /* printf, stderr, fprintf */
#include <unistd.h>  /* _exit, fork */
#include <stdlib.h>  /* exit */
#include <string.h>   /* errno */



int main(void)
{
 int i;
 int LeftRightChild=1;
 int level=2;
 puts("1");
 child_node(level,"1",LeftRightChild);


return(0);
}

int child_node (int level,const char* current_nod,int LeftRightChild)
{
int pid;
char Node[768],Node2[768];
char convert[768];
pid=fork();
if (LeftRightChild==1)

{
if (pid == 0)  // im the child
{
 sprintf(Node, "%d%s%d", level,current_nod,LeftRightChild);
 printf("%s\n",Node);
 LeftRightChild=LeftRightChild+1;
 child_node(level,current_nod,LeftRightChild);// gia to de3i paiditero paidi
}
}

else if (LeftRightChild==2)
{
if (pid == 0) // im the child
{
 sprintf(Node2, "%d%s%d", level,current_nod,LeftRightChild);
 printf("%s\n",Node2);
 LeftRightChild=LeftRightChild+1;
 child_node(level,Node,LeftRightChild);// gia to de3i paiditero paidi
}
}
else
{

    if (level<3)
    {
    puts("\n ");
    LeftRightChild=1;//gamao
    level=level+1;
    child_node(level,Node2,LeftRightChild);
    }
    else
    {

        exit(0);
    }
}
}
```

output atm is:
1
211
212

31
32

31
32

when it should look like 32111 32112 32121 32122 any ideas?

---

### Post by dwhitney67 on 2009-09-22
Here's another stab at the problem... once again, I am not using fork().
```

#include <stdio.h>   


void child_node(int level, const char* current_nod, int leftRightChild);

int main(void)
{
   int leftRightChild = 1;
   int level = 2;

   puts("1");

   child_node(level, "1", leftRightChild);

   return 0;
}

void child_node(int level, const char* curNode, int leftRightChild)
{
   char tmpNode[1024] = {0};

   if (level <= 3)
   {
      if (leftRightChild == 1)
      {
         sprintf(tmpNode, "%d.%s.%d", level, curNode, leftRightChild);

         puts(tmpNode);

         child_node(level, curNode, leftRightChild + 1);
      }
      else // if (leftRightChild == 2)
      {
         sprintf(tmpNode, "%d-%s-%d", level, curNode, leftRightChild);

         puts(tmpNode);
      }

      child_node(++level, tmpNode, 1);
   }
}

```

The output:
```

1
2.1.1
2-1-2
3.2-1-2.1
3-2-1-2-2
3.2.1.1.1
3-2.1.1-2

```


P.S.  A solution using fork()... for what it is worth:
```

#include <stdio.h>
#include <stdlib.h>
#include <unistd.h>


void child_node(int level, const char* current_nod, int leftRightChild);

int main(void)
{
   int leftRightChild = 1;
   int level = 2;

   puts("1");

   child_node(level, "1", leftRightChild);

   sleep(1);
   return 0;
}

void child_node(int level, const char* curNode, int leftRightChild)
{
   char tmpNode[1024] = {0};

   if (level <= 3)
   {
      if (leftRightChild == 1)
      {
         sprintf(tmpNode, "%d.%s.%d", level, curNode, leftRightChild);
         puts(tmpNode);

         if (fork() == 0)
         {
            child_node(level, curNode, leftRightChild + 1);
            exit(0);
         }

         child_node(++level, tmpNode, 1);
      }
      else //if (leftRightChild == 2)
      {
         sprintf(tmpNode, "%d-%s-%d", level, curNode, leftRightChild);
         puts(tmpNode);

         child_node(++level, tmpNode, 1);
      }
   }
}

```

---

### Post by Kotsouba on 2009-09-22
hm maybe i wasnt quite clear . i Have to use fork sadly its not a matter of choise :( ... OOps just seen the Fork() part of ur sollution thank you very much! giving it a try now ;)

---

### Post by dwhitney67 on 2009-09-22
That example using fork() can be simplified to the following:
```

#include <stdio.h>   // puts(), sprintf()
#include <stdlib.h>  // exit() 
#include <unistd.h>  // fork()


void child_node(int level, const char* current_nod, int leftRightChild);

int main(void)
{
   int leftRightChild = 1;
   int level = 2;

   puts("1");

   child_node(level, "1", leftRightChild);

   return 0;
}

void child_node(int level, const char* curNode, int leftRightChild)
{
   char tmpNode[1024] = {0};

   if (level <= 3)
   {
      sprintf(tmpNode, "%d.%s.%d", level, curNode, leftRightChild);
      puts(tmpNode);

      if (leftRightChild == 1 && fork() == 0)
      {
         child_node(level, curNode, leftRightChild + 1);
         exit(0);
      }

      child_node(++level, tmpNode, 1);
   }
}

```

---

### Post by Kotsouba on 2009-09-23
ok it works like a charm ;) now i got to modify sth i have to be able to make the tree custom height and grade meaning it may not be binary anymore. The height problem is solved easily by asking the user for a height and putting it in a variable but for changing the grade (assuming the tree is ordered , that every node has the same number of childs , i assume a loop is needed , i assume is not possible with more else ifs but maybe with case( )? any help greatly appreaciated ;)

---

