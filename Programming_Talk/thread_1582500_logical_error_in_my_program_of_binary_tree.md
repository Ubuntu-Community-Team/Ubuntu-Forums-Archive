---
title: "logical error in my program of binary tree"
date: 2010-09-26
forum: Programming Talk
---

### Post by jamesbon on 2010-09-26
I made a program to create a binary tree
```

#include<stdio.h>
#include<stdlib.h>
struct node {
    struct node *left, *right;
    int data, color;
} *root;
int check = 0;
typedef struct node tree;

tree *create_node(int);
void add_tree(tree *, tree *);
void travel_tree(tree *);
int main()
{
    int i, j, value;
    tree *nv;
    printf("enter value \n");
    scanf("%d", &value);
    nv = create_node(value);
    add_tree(nv, root);
    travel_tree(root);
}

tree *create_node(int num)
{
    tree *temp;
    if (check == 0) {
        root = (tree *) malloc(sizeof(tree));
        root->data = num;
        root->left = NULL;
        root->right = NULL;
        temp=root;
    }
    if (check != 0) {

        temp = (tree *) malloc(sizeof(tree));
        temp->data = num;
        temp->left = NULL;
        temp->right = NULL;

    }
    check++;
    return temp;
}

void add_tree(tree * something, tree * node)
{
    tree *ki;
    ki=node;
    if (check == 0)
        return;
    if ((something->data < ki->data) && (ki->left)) {
        add_tree(something, node->left);
    } else if ((something->data < ki->data) && (ki->left == NULL)) {
        //node left is to be added at last
        ki->left = something;
        return;
    }
    if ((something->data > node->data) && (ki->right)) {
        add_tree(something, node->right);
    }
    if ((something->data > ki->data) && (ki->right == NULL)) {
        //right node is to be added
        ki->right = something;
        return;
    }

}

void travel_tree(tree * temp)
{
    if (temp->left) {
        travel_tree(temp->left);
        printf(" %d", temp->data);
        return;
    }
    if (temp) {
        travel_tree(temp);
        printf(" %d", temp->data);
        return;
    }
    if (temp->right) {
        travel_tree(temp->right);
        printf(" %d", temp->data);
        return;
    }
}
```The logic is  I will create a node in function create_node and return a pointer to the node.
Will pass this pointer which will be in nv and root is initial call on add_tree function 
when it is called subsequently I am passing left or right sibling  depending upon the data in nv is greater or less than parent node to  left or right.
What is the error in above program.

PS: this is not a homework problem I just wrote a character device driver in this [thread]("http://ubuntuforums.org/showthread.php?t=1575088") I thought I should write some thing different hence trying my hands on it as in one previous thread some one thought it to be a homework problem.That is not the case.

---

### Post by GeneralZod on 2010-09-26
```

if (temp) {
        travel_tree(temp);
        printf(" %d", temp->data);
        return;
    }


```

causes a stack overflow.

---

### Post by jamesbon on 2010-09-26
How does it cause a stack overflow can you elaborate.

---

### Post by GeneralZod on 2010-09-26
> **jamesbon said:**
> How does it cause a stack overflow can you elaborate.

If we reach that statement, it will call travel_tree with temp (again) as the argument, which will reach that statement again (as it did last time), which will call travel_tree with (again) temp as the argument, which will reach that statement again (as it did last time), which will call travel_tree with (again) temp as the argument, which will reach that statement again (as it did last time), which will call travel_tree with (again) temp as the argument, which will reach that statement again (as it did last time), which will call travel_tree with (again) temp as the argument, etc until the stack overflows with calls to travel_tree with the same argument.

Run it in gdb to observe it in action.

---

### Post by jamesbon on 2010-09-26
Ok any other error in my logic you see?

---

### Post by GeneralZod on 2010-09-26
> **jamesbon said:**
> Ok any other error in my logic you see?

travel_tree doesn't appear to travel along the right hand side of a node if it travels down the left.

Frankly, I'd just start testing the thing at this point (i.e. - add a bunch of nodes with different values) and see what turns up.  

That "check" thing is a really odd and convoluted mechanism: why not ditch it (along with the "check == 0" half of create_node) and manually set root to a proper value in main()?

Edit:

Weird - I thought I'd pointed this out.  All this does at the moment is create a root node, and then (for some reason) try to add that root node to itself, which does nothing as root and root have the same "data" value.

---

### Post by trent.josephsen on 2010-09-26
You should make use of the code auditing tools you have available.  I have splint (which is free).
```
% splint test.c
Splint 3.1.2 --- 07 Sep 2009

test.c: (in function main)
test.c:18:5: Return value (type int) ignored: scanf("%d", &value)
  Result returned by function call is not used. If this is intended, can cast
  result to (void) to eliminate message. (Use -retvalint to inhibit warning)
test.c:22:2: Path with no return in function declared to return int
  There is a path through a function declared to return a value on which there
  is no return statement. This means the execution may fall through without
  returning a meaningful result to the caller. (Use -noret to inhibit warning)
test.c:22:2: Fresh storage nv not released before return
  A memory leak has been detected. Storage allocated locally is not released
  before the last reference to it is lost. (Use -mustfreefresh to inhibit
  warning)
   test.c:19:5: Fresh storage nv created
test.c:15:9: Variable i declared but not used
  A variable is declared but never used. Use /*@unused@*/ in front of
  declaration to suppress message. (Use -varuse to inhibit warning)
test.c:15:12: Variable j declared but not used
test.c: (in function create_node)
test.c:29:13: Arrow access from possibly null pointer root: root->data
  A possibly null pointer is dereferenced.  Value is either the result of a
  function which may return null (in which case, code should check it is not
  null), or a global, parameter or structure field declared with the null
  qualifier. (Use -nullderef to inhibit warning)
   test.c:28:16: Storage root may become null
test.c:37:13: Arrow access from possibly null pointer temp: temp->data
   test.c:36:16: Storage temp may become null
test.c:43:12: Variable temp used before definition
  An rvalue is used that may not be initialized to a value on some execution
  path. (Use -usedef to inhibit warning)
test.c:43:12: Dependent storage temp returned as implicitly only: temp
  Dependent storage is transferred to a non-dependent reference. (Use
  -dependenttrans to inhibit warning)
   test.c:43:12: Storage temp becomes dependent (through alias root)
test.c:43:17: Function returns with global root referencing released storage
  A global variable does not satisfy its annotations when control is
  transferred. (Use -globstate to inhibit warning)
   test.c:43:12: Storage root released
test.c: (in function add_tree)
test.c:52:41: Right operand of && is non-boolean (struct node *):
                 (something->data < ki->data) && (ki->left)
  The operand of a boolean operator is not a boolean. Use +ptrnegate to allow !
  to be used on pointers. (Use -boolops to inhibit warning)
test.c:56:9: Implicitly temp storage something assigned to implicitly only:
                ki->left = something
  Temp storage (associated with a formal parameter) is transferred to a
  non-temporary reference. The storage may be released or new aliases created.
  (Use -temptrans to inhibit warning)
test.c:59:43: Right operand of && is non-boolean (struct node *):
                 (something->data > node->data) && (ki->right)
test.c:64:9: Implicitly temp storage something assigned to implicitly only:
                ki->right = something
test.c: (in function travel_tree)
test.c:78:21: Null storage temp->left derivable from parameter travel_tree
                 (temp)
  A possibly null pointer is reachable from a parameter or global variable that
  is not declared using a /*@null@*/ annotation. (Use -nullstate to inhibit
  warning)
test.c:82:13: Arrow access from null pointer temp: temp->right
test.c:6:4: Variable exported but not used outside test: root
  A declaration is exported, but not used outside this module. Declaration can
  use static qualifier. (Use -exportlocal to inhibit warning)

test.c:10:7: Function exported but not used outside test: create_node
   test.c:44:1: Definition of create_node
test.c:11:6: Function exported but not used outside test: add_tree
   test.c:68:1: Definition of add_tree
test.c:12:6: Function exported but not used outside test: travel_tree
   test.c:87:1: Definition of travel_tree

Finished checking --- 20 code warnings
```

Some of these are downright confusing, so I'll translate for you: **always** check the return values of functions; make your success or failure explicit in main; be sure to free() everything you malloc(); don't declare variables you don't use; validate your pointers before dereferencing them; be careful to initialize everything before you use it; don't assign temporary storage to permanent references; and use `static' for functions that you don't use outside of a file.

In general, lint and similar tools will catch quite a few logic errors and subtle bugs.  Human code auditing is more useful for identifying common usage patterns and fixing stylistic problems.  For example, splint tells you that you have a memory leak and could accidentally dereference a null pointer, but I will tell you that this pattern:
```
if (check == 0) {
    ...
}
if (check != 0) {
    ...
}
```
would be better written as if (check) { ... } else { ... }; that your indentation is atrocious; that you shouldn't use scanf; and that you probably want to reconsider using a global "check" state for a problem that doesn't demand it.

Just a few thoughts.  I haven't even given any thought to what the program actually does, so I'm not considering contextual demands, just things that popped into my head while skimming it.

---

### Post by jamesbon on 2010-09-27
> **GeneralZod said:**
> If we reach that statement, it will call  travel_tree with temp (again) as the argument, which will reach that  statement again (as it did last time), which will call travel_tree with  (again) temp as the argument, which will reach that statement again (as  it did last time), which will call travel_tree with (again) temp as the  argument, which will reach that statement again (as it did last time),  which will call travel_tree with (again) temp as the argument, which  will reach that statement again (as it did last time), which will call  travel_tree with (again) temp as the argument, etc until the stack  overflows with calls to travel_tree with the same argument.

Run it in gdb to observe it in action.
Yes you are right this is happening.
But I could not understand this fully.
Will the same segmentation fault not happen for temp->left or temp->right ?

---

### Post by dwhitney67 on 2010-09-27
GeneralZod is correct; why are you using the "check" variable to keep state?

Perhaps if you initialize your pointers to something meaningful, you could check those.

Consider the following (which may or may not compile):
```

typedef struct node
{
   int          data;
   //int          color;

   struct node* left;
   struct node* right;
} Node;


Node* addNode(Node* root, int data);


int main()
{
   Node* tree_root = 0;   // always initialize pointers!
   int   num = 0;

   printf("Enter a number: ");
   scanf("%d", &num);

   tree_root = addNode(tree_root, num);
   tree_root = addNode(tree_root, 5);
   tree_root = addNode(tree_root, 3);
   tree_root = addNode(tree_root, 10);

   ...

   return 0;
}

Node* addNode(Node* root, int num)
{
   if (root == 0)
   {
      root = malloc(sizeof(Node));

      root->data  = num;
      root->left  = 0;
      root->right = 0;
   }
   else
   {
      if (num < root->data)
      {
         root->left = addNode(root->left, num);
      }
      else if (num > root->data)
      {
         root->right = addNode(root->right, num);
      }

      /* TODO: determine if we should allow duplicate num values in tree. */
   }

   return root;
}

```

P.S.  I have not tested the code above, much less compiled it.

---

### Post by r-senior on 2010-09-27
Have you tried running it with a debugger? I just stepped through it and your segfault seems to be on line 88. I've not picked through it but judging by the way it brought my Eclipse IDE to its knees I'd suspect infinite recursion?

```

void travel_tree(tree * temp)
{
    if (temp->left) {
        travel_tree(temp->left);
        printf(" %d", temp->data);
        return;
    }
    if (temp) {
        travel_tree(temp);              // <<< line 88
        printf(" %d", temp->data);
        return;
    }

```

EDIT: I do apologise for duplication. Some recent posts weren't showing up for me.

---

### Post by GeneralZod on 2010-09-27
> **jamesbon said:**
> Will the same segmentation fault not happen for temp->left or temp->right ?

No: This would require that your "tree" has loops in it (i.e. that there is a node and a sequence of left's and rights starting from that node that, when followed, led back to that node) in which case the tree wouldn't be a tree (one of the defining properties of a tree is that it contains no such loops).

---

### Post by jamesbon on 2010-09-27
If I do root=NULL as
```

typedef struct node tree;
root=NULL;
tree *create_node(int);
void add_tree(int value, tree *);
void travel_tree(tree *);
int main()


```
then I get a lot of warnings.
```

tree.c:9: warning: data definition has no type or storage class
tree.c:9: error: conflicting types for &#8216;root&#8217;
tree.c:6: note: previous declaration of &#8216;root&#8217; was here
tree.c:9: warning: initialization makes integer from pointer without a cast
tree.c: In function &#8216;main&#8217;:
tree.c:21: warning: passing argument 2 of &#8216;add_tree&#8217; makes pointer from integer without a cast
tree.c:11: note: expected &#8216;struct tree *&#8217; but argument is of type &#8216;int&#8217;
tree.c:23: warning: passing argument 1 of &#8216;travel_tree&#8217; makes pointer from integer without a cast
tree.c:12: note: expected &#8216;struct tree *&#8217; but argument is of type &#8216;int&#8217;
tree.c: In function &#8216;add_tree&#8217;:
tree.c:40: warning: comparison between pointer and integer
tree.c:41: warning: assignment makes integer from pointer without a cast
tree.c:43: error: invalid type argument of &#8216;->&#8217; (have &#8216;int&#8217;)

```

if I do 
```

#include<stdio.h>
#include<stdlib.h>
struct node {
        struct node *left, *right;
        int data, color;
} *root=NULL;
int check = 0;

```
then all these errors and warnings go.
Can I not initialize a global pointer root=NULL before main.
If the program has
 initialized root=NULL at structure definition itself does not give any error to compile
```

#include<stdio.h>
#include<stdlib.h>
struct node {
    struct node *left, *right;
    int data, color;
} *root=NULL;
int check = 0;
typedef struct node tree;
tree *create_node(int);
void add_tree(int value, tree *);
void travel_tree(tree *);
int main()
{
    int i, j, value;
    tree *nv;
    printf("enter value \n");
    while (scanf("%d", &value) != 1) {
        printf("enter value \n");
        nv = create_node(value);
        add_tree(value, root);
    }
    travel_tree(root);
}

tree *create_node(int num)
{
    tree *temp;

    temp = (tree *) malloc(sizeof(tree));
    temp->data = num;
    temp->left = NULL;
    temp->right = NULL;
    return temp;

}

void add_tree(int v1, tree * node)
{
    if (root == NULL) {
        root = create_node(v1);
        return;
    printf("\n data of root %d",root->data);
    }
    if ((v1 < node->data) && (node->left)) {
        add_tree(v1, node->left);
        node->left = create_node(v1);
        return;
    }
    if ((v1 > node->data) && (node->right)) {
        add_tree(v1, node->right);
        node->right = create_node(v1);
        return;
    }
}

void travel_tree(tree * temp)
{
    printf("\n inside travel_tree");

    if (temp->left) {
        travel_tree(temp->left);
        printf(" %d", temp->data);
        return;
    }
    printf("  %d ", temp->data);
    if (temp->right) {
        travel_tree(temp->right);
        printf(" %d", temp->data);
        return;
    }
    if ((temp->left == NULL) && (temp->right == NULL)) {
        printf("it is only root node %d", temp->data);
    }
}

```
 but gives a segmentation fault.
```

Program received signal SIGSEGV, Segmentation fault.
0x00000000004007a8 in travel_tree (temp=0x0) at tree.c:60
60        if (temp->left) {

```
Why is this happening and how can I over come it?

---

### Post by jamesbon on 2010-09-27
paste error.

---

### Post by dwhitney67 on 2010-09-27
> **jamesbon said:**
> Ok I modified the program but still it does not work as binary tree


Were you ever able to give a try to the [code]("http://ubuntuforums.org/showpost.php?p=9895058&postcount=9") I posted earlier?

---

### Post by jamesbon on 2010-09-27
> **dwhitney67 said:**
> Were you ever able to give a try to the [code]("http://ubuntuforums.org/showpost.php?p=9895058&postcount=9") I posted earlier?
No I did not tried that but I saw you initialized the root pointer to 0 which in my case I have done NULL.
I am trying to understand what is the fault in my program.
```

#include<stdio.h>
#include<stdlib.h>
struct node {
    struct node *left, *right;
    int data, color;
} *root;
int check = 0;
typedef struct node tree;
tree *create_node(int);
void add_tree(int value, tree *);
void travel_tree(tree *);
int main()
{
    int i, j, value;
    tree *nv;
    root=NULL;
    printf("enter value \n");
    while (scanf("%d", &value) != 1) {
        printf("enter value \n");
        nv = create_node(value);
        add_tree(value, root);
    }
    travel_tree(root);
}

tree *create_node(int num)
{
    tree *temp;

    temp = (tree *) malloc(sizeof(tree));
    temp->data = num;
    temp->left = NULL;
    temp->right = NULL;
    return temp;

}

void add_tree(int v1, tree * node)
{
    if (root == NULL) {
        root = create_node(v1);
        return;
    printf("\n data of root %d",root->data);
    }
    if ((v1 < node->data) && (node->left)) {
        add_tree(v1, node->left);
        node->left = create_node(v1);
        return;
    }
    if ((v1 > node->data) && (node->right)) {
        add_tree(v1, node->right);
        node->right = create_node(v1);
        return;
    }
}

void travel_tree(tree * temp)
{
    printf("\n inside travel_tree");

    if (temp->left) {
        travel_tree(temp->left);
        printf(" %d", temp->data);
        return;
    }
    printf("  %d ", temp->data);
    if (temp->right) {
        travel_tree(temp->right);
        printf(" %d", temp->data);
        return;
    }
    if ((temp->left == NULL) && (temp->right == NULL)) {
        printf("it is only root node %d", temp->data);
    }
}

```Is above code which I am trying
and I got a segmentation fault in gdb as
```

0x00000000004007b3 in travel_tree (temp=0x0) at tree.c:61
61        if (temp->left) {

```

The value of global pointer root is always 0x0 as gdb shows
```

(gdb) print temp->left
Cannot access memory at address 0x0
(gdb) print temp
$1 = (tree *) 0x0
(gdb) print root
$2 = (struct node *) 0x0

```
no matter where I use it and where I pass it.
Why is that happening? Did I do some mistake?

---

### Post by GeneralZod on 2010-09-27
If the user enters a single valid number and presses enter, the body of your while loop will not be executed, so root is NULL when you call to travel_tree(root), which has no guard against its input being NULL.

---

### Post by jamesbon on 2010-09-27
Ok I modified the code now it is 
```

#include<stdio.h>
#include<stdlib.h>
struct node {
    struct node *left, *right;
    int data, color;
} *root;
int check = 0;
typedef struct node tree;
tree *create_node(int);
void add_tree(int value, tree *);
void travel_tree(tree *);
int main()
{
    int i, j, value;
    tree *nv;
    root=NULL;
    value=0;
    while ( value != 1) {
        printf("enter value \n");
        scanf("%d",&value);
        if(root==NULL)
        root=create_node(value);
        else if(root!=NULL){

        add_tree(value, root);
             }
    }
    travel_tree(root);
}

tree *create_node(int num)
{
    tree *temp;

    temp = (tree *) malloc(sizeof(tree));
    temp->data = num;
    temp->left = NULL;
    temp->right = NULL;
    return temp;

}

void add_tree(int v1, tree * node)
{
    if ((v1 < node->data) && (node->left)) {
        add_tree(v1, node->left);
        node->left = create_node(v1);
        return;
    }
    if ((v1 > node->data) && (node->right)) {
        add_tree(v1, node->right);
        node->right = create_node(v1);
        return;
    }
}

void travel_tree(tree * temp)
{
    printf("\n inside travel_tree");

    if (temp->left) {
        travel_tree(temp->left);
        printf(" %d", temp->data);
        return;
    }
    printf("  %d ", temp->data);
    if (temp->right) {
        travel_tree(temp->right);
        printf(" %d", temp->data);
        return;
    }
    if ((temp->left == NULL) && (temp->right == NULL)) {
        printf("it is only root node %d", temp->data);
    }
}

```but it is not able to print the tree what can be the reason now?

---

### Post by GeneralZod on 2010-09-27
add_tree does not handle the case where node's (root's, in this case) left and right branches are both NULL, so it cannot add any values to the tree beginning with root.

I suggest you practice [dry runs](http://en.wikipedia.org/wiki/Dry_run_(testing)), or at least do a run of the programming and follow the steps with gdb.

---

### Post by jamesbon on 2010-09-27
Ok I modified and included the conditions as you said.
The last error which I am seeing is in inorder traversal.
```

#include<stdio.h>
#include<stdlib.h>
struct node {
    struct node *left, *right;
    int data, color;
} *root;
int check = 0;
typedef struct node tree;
tree *create_node(int);
void add_tree(int value, tree *);
void travel_tree(tree *);
int main()
{
    int i, j, value;
    tree *nv;
    root = NULL;
    value = 0;
    while (value != 1) {
        printf("enter value \n");
        scanf("%d", &value);
        if (root == NULL)
            root = create_node(value);
        else if (root != NULL) {
            //      nv = create_node(value);
            add_tree(value, root);
        }
    }
    travel_tree(root);
}

tree *create_node(int num)
{
    tree *temp;

    temp = (tree *) malloc(sizeof(tree));
    temp->data = num;
    temp->left = NULL;
    temp->right = NULL;
    return temp;

}

void add_tree(int v1, tree * node)
{

    if (v1 < node->data) {
        if (node->left != NULL) {
            add_tree(v1, node->left);
            node->left = create_node(v1);
        } else {
            node->left = create_node(v1);
        }
        return;
    }
    if (v1 > node->data) {
        if (node->right != NULL) {
            add_tree(v1, node->right);
            node->right = create_node(v1);
        } else {
            node->right = create_node(v1);
        }
        return;
    }
}

void travel_tree(tree * temp)
{
    printf("\n inside travel_tree");

    if (temp->left!=NULL) {
        travel_tree(temp->left);
        printf(" %d", temp->data);
        return;
    }
    printf("  %d ", temp->data);
    if (temp->right!=NULL) {
        travel_tree(temp->right);
        printf(" %d", temp->data);
        return;
    }
}
```

---

### Post by GeneralZod on 2010-09-27
Ok, I have a fixed copy of your program here, but I'm not going to tell you what it is :)

There are errors in add_tree, and travel_tree.

I'll ask you to simulate, with pen and paper and your brain, what would happen if the user entered the following:

```

5 9 7 3 8 1

```

Don't worry about the travel_tree for now: what would the tree look like if the user entered that sequence into your program? How many nodes would there be?

---

### Post by jamesbon on 2010-09-27
By the time your message came I had improved it a bit more
here is it
```

#include<stdio.h>
#include<stdlib.h>
struct node {
    struct node *left, *right;
    int data, color;
} *root;
int check = 0;
typedef struct node tree;
tree *create_node(int);
void add_tree(int value, tree *);
void travel_tree(tree *);
int main()
{
    int i, j, value;
    tree *nv;
    root = NULL;
    value = 0;
    while (1==1) {
        printf("enter value \n");
        scanf("%d", &value);
        if(value==1)
        break;
        if (root == NULL)
            root = create_node(value);
        else if (root != NULL) {
            //      nv = create_node(value);
            add_tree(value, root);
        }
    }
    travel_tree(root);
}

tree *create_node(int num)
{
    tree *temp;

    temp = (tree *) malloc(sizeof(tree));
    temp->data = num;
    temp->left = NULL;
    temp->right = NULL;
    return temp;

}

void add_tree(int v1, tree * node)
{

    if (v1 < node->data) {
        if (node->left != NULL) {
            add_tree(v1, node->left);
            node->left = create_node(v1);
        } else {
            node->left = create_node(v1);
        }
        
    }
    if (v1 > node->data) {
        if (node->right != NULL) {
            add_tree(v1, node->right);
            node->right = create_node(v1);
        } else {
            node->right = create_node(v1);
        }
        
    }
    return;
}

void travel_tree(tree * temp)
{
//    printf("\n inside travel_tree");

    if (temp->left!=NULL) {
        travel_tree(temp->left);
//        printf(" %d", temp->data);
        
    }
    printf("  %d ", temp->data);
    if (temp->right!=NULL) {
        travel_tree(temp->right);
//        printf(" %d", temp->data);
        
    }
    return;
}

```
Did you mean the return statements in add_tree and travel_tree functions
I am trying your above input.Till the time you can go through above section which is improved code.

---

### Post by GeneralZod on 2010-09-27
Your new travel_tree looks good :)

---

### Post by jamesbon on 2010-09-28
Ya :)
 I found the previous program were having problem in add_node function since after adding a node when it returns to the previous instance of add_node which called the current 
it goes down and checked if(v1>node->right) and if it exist it will create a node irrespective of the fact it has already traveled the tree once to add.


Here is the new program
```

#include<stdio.h>
#include<stdlib.h>
struct node {
	struct node *left, *right;
	int data, color;
} *root;
int check = 0;
typedef struct node tree;
tree *create_node(int);
void add_tree(int value, tree *);
void travel_tree(tree *);
int main()
{
	int i, j, value;
	tree *nv;
	root = NULL;
	value = 0;
	while (1==1) {
		printf("enter value \n");
		scanf("%d", &value);
		if(value==1)
		break;
		if (root == NULL)
			root = create_node(value);
		else if (root != NULL) {
			//      nv = create_node(value);
			add_tree(value, root);
		}
	}
	travel_tree(root);
}

tree *create_node(int num)
{
	tree *temp;

	temp = (tree *) malloc(sizeof(tree));
	temp->data = num;
	temp->left = NULL;
	temp->right = NULL;
	return temp;

}

void add_tree(int v1, tree * node)
{

	if (v1 <= node->data) {
		if (node->left != NULL) {
			add_tree(v1, node->left);
		} else {
			node->left = create_node(v1);
		}
	return;	
	}
	if (v1>node->data)  {
		if (node->right != NULL) {
			add_tree(v1, node->right);
		} else {
			node->right = create_node(v1);
		}
	return;	
	}
	
}

void travel_tree(tree * temp)
{
//	printf("\n inside travel_tree");

	if (temp->left!=NULL) 
	travel_tree(temp->left);
	printf(" \n %d ", temp->data);
	if (temp->right!=NULL) 
	travel_tree(temp->right);
	return;
}

```

This new program  which I just posted 
used your input 5 9 7 3 8 1
 the output I am getting is 
3 5 7 8 9
is this correct as last 1 is to come out of tree.

---

### Post by GeneralZod on 2010-09-29
> **jamesbon said:**
> 
This new program  which I just posted 
used your input 5 9 7 3 8 1
 the output I am getting is 
3 5 7 8 9
is this correct as last 1 is to come out of tree.

Great :) Yes, that's correct: the "1" just exits the loop, and is never added to the tree (this seemed to be what you were aiming for based on your earlier code).

---

