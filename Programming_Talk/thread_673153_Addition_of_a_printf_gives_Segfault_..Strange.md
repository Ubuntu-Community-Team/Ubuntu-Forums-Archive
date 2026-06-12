---
title: "Addition of a printf gives Segfault ..Strange"
date: 2008-01-20
forum: Programming Talk
---

### Post by shakeeb on 2008-01-20
Hi
I can run the following snippet of code fine, that is until i add a trivial printf statement 
in the insert function. Any help is appreciated. 

```
#include<stdio.h>
#include<malloc.h>
#include<math.h>

typedef struct BST{
	int element;
	int height;
	struct BST* left;
	struct BST* right;
	int useless;

}Tree;
int max ( int a , int b){
	if(a > b)
		return a;
	return b;
	}
int height(Tree *root){
	if (root==NULL)
		return -1;
	else
	return root->height;
}
Tree* Insert(Tree* root, int value){
	int temp1;
	if(root==NULL){
		root=(Tree*)malloc(sizeof(Tree));
		root->element=value;
		root->height=0;
		return root;
	}
	else{
		if(root){
			if(root->element > value){
				root->left=Insert(root->left,value);
				root->height=max(height(root->left),height(root->right))+1;
				root->useless=54;
			**#printf("This printf causes Segfault");	**
			
		}
		else{
			if(root->element < value){
				root->right=Insert(root->right,value);
				root->height=max(height(root->left),height(root->right))+1;
			}
			
			}

			
		}


}
}

void InorderPrint(Tree *root){
		
		if (root->left){
			InorderPrint(root->left);
			}
		printf("%3d  %d\n",root->element, root->height);
		if (root->right){
			InorderPrint(root->right);
			}
		

}
int main(){
	
	Tree *root=(Tree*)malloc(sizeof(Tree));
	root->element=23;
	Tree *temp=root;
	Insert(temp,15);
	Insert(temp,25);
	Insert(temp,36);
	Insert(temp,24);
	Insert(temp,17);
	Insert(temp,14);
	Insert(temp,111);
	
InorderPrint(temp);
}

```:confused:

---

### Post by shakeeb on 2008-01-20
Hi
I can run the following snippet of code fine, that is until i add a trivial printf statement 
in the insert function. Any help is appreciated. 

```
#include<stdio.h>
#include<malloc.h>
#include<math.h>

typedef struct BST{
	int element;
	int height;
	struct BST* left;
	struct BST* right;
	int useless;

}Tree;
int max ( int a , int b){
	if(a > b)
		return a;
	return b;
	}
int height(Tree *root){
	if (root==NULL)
		return -1;
	else
	return root->height;
}
Tree* Insert(Tree* root, int value){
	int temp1;
	if(root==NULL){
		root=(Tree*)malloc(sizeof(Tree));
		root->element=value;
		root->height=0;
		return root;
	}
	else{
		if(root){
			if(root->element > value){
				root->left=Insert(root->left,value);
				root->height=max(height(root->left),height(root->right))+1;
				root->useless=54;
			**#printf("This printf causes Segfault");	**
			
		}
		else{
			if(root->element < value){
				root->right=Insert(root->right,value);
				root->height=max(height(root->left),height(root->right))+1;
			}
			
			}

			
		}


}
}

void InorderPrint(Tree *root){
		
		if (root->left){
			InorderPrint(root->left);
			}
		printf("%3d  %d\n",root->element, root->height);
		if (root->right){
			InorderPrint(root->right);
			}
		

}
int main(){
	
	Tree *root=(Tree*)malloc(sizeof(Tree));
	root->element=23;
	Tree *temp=root;
	Insert(temp,15);
	Insert(temp,25);
	Insert(temp,36);
	Insert(temp,24);
	Insert(temp,17);
	Insert(temp,14);
	Insert(temp,111);
	
InorderPrint(temp);
}

```:confused:

Iam using gutsy btw.

---

### Post by shakeeb on 2008-01-20
It Segfaults in height according to gdb.
But height is absoultely seg fault proof as i see it.

---

### Post by Paulmd on 2008-01-20
What's with the '#' in front of the printf?? That's not how you do comments in c.

---

### Post by shakeeb on 2008-01-20
> **Paulmd said:**
> What's with the '#' in front of the printf?? That's not how you do comments in c.
too much python i guess...that was added just for the post .....

---

### Post by LaRoza on 2008-01-20
Your code is difficult to read, the indents are odd.

I changed "printf" to "puts" to see what would happen, it printed twice, then a seg fault.

Perhaps you shouldn't be printing in that function, have the calling function print.


The following code still seg faults, after two prints, but is much easier to read.
[php]
Tree* Insert(Tree* root, int value)
{
	int temp1;
	if(root==NULL)
    {
		root=(Tree*)malloc(sizeof(Tree));
		root->element=value;
		root->height=0;
		return root;
	}
	else
    {
		if(root)
        {
			if(root->element > value)
            {
				root->left=Insert(root->left,value);
				root->height=max(height(root->left),height(root->right))+1;
				root->useless=54;
			    puts("This printf causes Segfault");
            
			
		    }
		    else if(root->element < value)
            {
				root->right=Insert(root->right,value);
				root->height=max(height(root->left),height(root->right))+1;
			}
			
	    }

			
    }


}
[/php]

---

### Post by Paulmd on 2008-01-20
> **LaRoza said:**
> Your code is difficult to read, the indents are odd.

I changed "printf" to "puts" to see what would happen, it printed twice, then a seg fault.

Perhaps you shouldn't be printing in that function, have the calling function print.


The following code still seg faults, after two prints, but is much easier to read.
[php]
Tree* Insert(Tree* root, int value)
{
	int temp1;
	if(root==NULL)
    {
		root=(Tree*)malloc(sizeof(Tree));
		root->element=value;
		root->height=0;
		return root;
	}
	else
    {
		if(root)
        {
			if(root->element > value)
            {
				root->left=Insert(root->left,value);
				root->height=max(height(root->left),height(root->right))+1;
				root->useless=54;
			    puts("This printf causes Segfault");
            
			
		    }
		    else if(root->element < value)
            {
				root->right=Insert(root->right,value);
				root->height=max(height(root->left),height(root->right))+1;
			}
			
	    }

			
    }


}
[/php]

the following is equivilent logic

[php]

Tree* Insert(Tree* root, int value)
{
    int temp1;
    if(root==NULL)
    {
        root=(Tree*)malloc(sizeof(Tree));
        root->element=value;
        root->height=0;
        return root;
    }
    /* if root IS null, then this code doesn't get executed because the function would have already returned, the extra logic was superfluous*/

    if(root->element > value)
    {
        root->left=Insert(root->left,value);
        root->height=max(height(root->left),height(root->right))+1;
        root->useless=54;
        puts("This printf causes Segfault");
     }
     else if(root->element < value)
     {
         root->right=Insert(root->right,value);
         root->height=max(height(root->left),height(root->right))+1;
      }

   /* Note: nothing happens AT ALL, to left, right, or height if root->element==value. Is this what you want?*/
            
}  
[/php]

---

### Post by LaRoza on 2008-01-20
> **Paulmd said:**
> the following is equivilent logic

[php]

Tree* Insert(Tree* root, int value)
{
    int temp1;
    if(root==NULL)
    {
        root=(Tree*)malloc(sizeof(Tree));
        root->element=value;
        root->height=0;
        return root;
    }
    /* if root IS null, then this code doesn't get executed because the function would have already returned, the extra logic was superfluous*/

    if(root->element > value)
    {
        root->left=Insert(root->left,value);
        root->height=max(height(root->left),height(root->right))+1;
        root->useless=54;
        puts("This printf causes Segfault");
     }
     else if(root->element < value)
     {
         root->right=Insert(root->right,value);
         root->height=max(height(root->left),height(root->right))+1;
      }

   /* Note: nothing happens AT ALL, to left, right, or height if root->element==value. Is this what you want?*/
            
}  
[/php]

Quite true.

Also, the function claims to return a pointer to Tree, but doesn't always. It seems it shouldn't be returning anything other than an error code (probably an int)

---

### Post by shakeeb on 2008-01-20
> /* if root IS null, then this code doesn't get executed because the function would have already returned, the extra logic was superfluous*/ 
Thanks for that ...
> 
   /* Note: nothing happens AT ALL, to left, right, or height if root->element==value. Is this what you want?*/ 
This is fine for the time being since my input is distinct, once the seg fault is fixed ,it can be handled.

---

### Post by shakeeb on 2008-01-20
This is the gdb output

```

Starting program: ~/DS/a.out 
This printf causes Segfault
This printf causes Segfault

Program received signal SIGSEGV, Segmentation fault.
0x0804840d in height ()

```

I can't see height() segfaulting in anyway !!!.

---

### Post by LaRoza on 2008-01-20
It seems to me, this function shouldn't be printing. Have it return an error code, then process that in the calling function.

---

### Post by geirha on 2008-01-20
Insert doesn't return anything if root != null ...

---

### Post by LaRoza on 2008-01-20
[http://ubuntuforums.org/showthread.php?t=673144](http://ubuntuforums.org/showthread.php?t=673144)

---

### Post by shakeeb on 2008-01-20
thats it thanks... 
I moved the return root to the last line of the function...but I don't understand why it happens though....

---

### Post by shakeeb on 2008-01-20
I moved the return root to the last line of the Insert function and it works absolutely fine  .
I don't understand why though.

---

### Post by Paulmd on 2008-01-20
> **LaRoza said:**
> Quite true.

Also, the function claims to return a pointer to Tree, but doesn't always. It seems it shouldn't be returning anything other than an error code (probably an int)

AHA! I think you nailed it. In fact, the only time it returns a valid value is when root==NULL. 

I THINK root is supposed to be null for all cases that the function is called recursively. But recursion can be evil. With a real programming environment, you could step through the code to see what's happening. It could be a case of infinite recursion or some other evil.

---

### Post by asmoore82 on 2008-01-20
every function that has a non-void return type needs to return something(esp. main())

The Insert function only has a return value If something was NULL;
I don't think this could be causing the segfault since the return value
of Insert() doesn't seem to be used anywhere, but it's still a problem.

I read once in the old days that ALL mains in C should be of return type **int**
and should always return 0(zero) on success. Personally, back when I started C,
I did the **int** return type but I would return 1 on success(Boolean "True").
I later found out that the 0 is overall better practice because UNIX shells will
expect a 0 return value on success.

---

### Post by Paulmd on 2008-01-20
> **asmoore82 said:**
> every function that has a non-void return type needs to return something(esp. main())

The Insert function only has a return value If something was NULL;
I don't think this could be causing the segfault since the return value
of Insert() doesn't seem to be used anywhere, but it's still a problem.

I read once in the old days that ALL mains in C should be of return type **int**
and should always return 0(zero) on success. Personally, back when I started C,
I did the **int** return type but I would return 1 on success(Boolean "True").
I later found out that the 0 is overall better practice because UNIX shells will
expect a 0 return value on success.

the return value of Insert() IS being used, within the Insert() function itself. A recursive call.

---

### Post by wolfbone on 2008-01-20
> **shakeeb said:**
> thats it thanks... 
I moved the return root to the last line of the function...but I don't understand why it happens though....

Because you are returning the int coming from printf() as a (Tree *) - as has been pointed out in the duplicate thread.

There is nothing strange about this program segfaulting!

---

### Post by bapoumba on 2008-01-20
Threads merged.

---

