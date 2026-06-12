---
title: "array of structure pointers"
date: 2012-05-27
forum: Programming Talk
---

### Post by jamesbon on 2012-05-27
I am trying to make a graph this program is just in initial phases where I 
 declared an array of structure pointers which holds address of vertices
 *vertices[20] is an array which whose elements are all addresses of type  struct node * which will contain the address of node of graphs.

```
    #include<stdio.h>
    #include<stdlib.h>
    struct node {
    	int data;
    	struct node *links[10];
    };
    struct node *create_node(int);
    void create_vertices(struct node **);
    int main()
    {
    	struct node *vertices[20];
    	int d, i, choice;
            *vertices[0]=(struct node *)malloc(sizeof(struct node)*20);
            create_vertices (&vertices);
    }
    
    struct node *create_node(int data)
    {
    	int i;
    	struct node *temp = (struct node *)malloc(sizeof(struct node));
    	temp->data = data;
    	for (i = 0; i < 10; i++)
    		temp->links[i] = NULL;
    	return temp;
    }
    
    void create_vertices (struct node **v)
    {
     int i,choice;
     i=0;
    	printf("enter choice\n");
    	scanf("%d", &choice);
    	while (choice == 1) {
    		printf("enter data\n");
    		scanf("%d", &d);
    		vertices[i] = create_node(d);
    		i++;
    		printf("enter choice\n");
    		scanf("%d", &choice);
    	}
    }

```


Compiling the above code gives me following errors


```
    bfs.c: In function ‘main’:
    bfs.c:13:21: error: incompatible types when assigning to type ‘struct node’ from type ‘struct node *’
    bfs.c:14:9: warning: passing argument 1 of ‘create_vertices’ from incompatible pointer type [enabled by default]
    bfs.c:8:6: note: expected ‘struct node **’ but argument is of type ‘struct node * (*)[20]’
    bfs.c: In function ‘create_vertices’:
    bfs.c:35:16: error: ‘d’ undeclared (first use in this function)
    bfs.c:35:16: note: each undeclared identifier is reported only once for each function it appears in
    bfs.c:36:3: error: ‘vertices’ undeclared (first use in this function)

```


the program says an error in following line

```
    	struct node *vertices[20];
    *vertices[0]=(struct node *)malloc(sizeof(struct node)*20);

```
what is the harm in this kind of declaration.
I declare an array of pointers of type struct node * should I not give memory also to them.

I have a confusion here how will vertices[1] be stored because if I give all the memory to vertices[0] what I am trying to do is create an array vertices[0],vertices[1],vertices[2],vertices[3] and so on I am trying to use malloc for the same.

---

### Post by Bachstelze on 2012-05-27
```
#include <stdio.h>
#include <stdlib.h>

struct node {
    int data;
    struct node *links[10];
};

struct node *create_node(int);
void create_vertices(struct node **);

int main(void)
{
    struct node *vertices[20];
    create_vertices (vertices);
}

struct node *create_node(int data)
{
    int i;
    struct node *temp = malloc(sizeof(struct node));
    temp->data = data;
    for (i = 0; i < 10; i++)
        temp->links[i] = NULL;
    return temp;
}

void create_vertices (struct node **v)
{
    int i, d, choice;
    i=0;
    printf("enter choice\n");
    scanf("%d", &choice);
    while (choice == 1) {
        printf("enter data\n");
        scanf("%d", &d);
        v[i] = create_node(d);
        i++;
        printf("enter choice\n");
        scanf("%d", &choice);
    }
}

```

---

