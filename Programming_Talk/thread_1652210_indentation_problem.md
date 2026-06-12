---
title: "indentation problem"
date: 2010-12-24
forum: Programming Talk
---

### Post by jamesbon on 2010-12-24
Hi,
I am trying to indent my program.I did read the man page of indent but there are so many options that I could not understand.I read wikipedia page of indentation styles.
Following is my code 
```

#include "declarations.h"
graph root = NULL;

int main()
{
    cgraph();
}

void cgraph(void)
{
    int n, choice, dir, count, sib;

    choice = 1;
    count = 1;
    graph priv, temp;

    printf("Printf we are making a graph the first is root node\n");
    while (choice == 1) {
        count++;
        if (count == 1) {
            printf("This is going to be root node \n");
            scanf("%d", &n);
            root = cnode(n);
            count--;
            priv = root;
        }        //ending if
        else {
            printf("Enter the number of siblings to this node\n");
            scanf("%d", &sib);
            while (sib > 0) {
                printf
                    ("Enter direction you want to go LEFT 1 RIGHT 2 TOP 3 DOWN 4\n");
                scanf("%d", &dir);
                printf("Enter the data  for graph node\n");
                scanf("%d", &n);
                temp = cnode(n);
                if (dir == 1) {
                    priv->LEFT = temp;
                }
                if (dir == 2) {
                    priv->RIGHT = temp;
                }
                if (dir == 3) {
                    priv->TOP = temp;
                }
                if (dir == 4) {
                    priv->DOWN = temp;
                }
                sib--;
            }    //ending while of sibling
            priv = temp;    //priv is equal to which temp?
        }        //ending else
        [B]printf
            ("Enter 1 to continue adding nodes to graph any thing else would take you out\n");[/B]
        scanf("%d", &choice);
    }            //ending while
}                //ending main

graph cnode(int data)
{
    graph temp = (graph) malloc(sizeof(graph));

    temp->data = data;
    temp->LEFT = NULL;
    temp->RIGHT = NULL;
    temp->TOP = NULL;
    temp->DOWN = NULL;
    temp->color = -1;
    return temp;
}

qnode travel_graph(graph rh)
{
    qnode qt;
    if (rh->LEFT) {
        qt = cque(rh);
    }
    if (rh->RIGHT) {
        qt = cque(rh);
    }
    if (rh->TOP) {
        qt = cque(rh);
    }
    if (rh->DOWN) {
        qt = cque(rh);
    }
    return qt;
}

```

I want to achieve the style as the guy [here]("http://stackoverflow.com/questions/3905238/opening-curly-bracket-brace-position-on-code/4527333#4527333") has discussed.But in my case when I try 
indent -linux graph.c
You can see the printf statement which I highlighted has broken to next line.
I do not want this to happen so what should I use from indent's man page.

---

### Post by Arndt on 2010-12-24
> **jamesbon said:**
> Hi,
I am trying to indent my program.I did read the man page of indent but there are so many options that I could not understand.I read wikipedia page of indentation styles.
Following is my code 
```

#include "declarations.h"
graph root = NULL;

int main()
{
    cgraph();
}

void cgraph(void)
{
    int n, choice, dir, count, sib;

    choice = 1;
    count = 1;
    graph priv, temp;

    printf("Printf we are making a graph the first is root node\n");
    while (choice == 1) {
        count++;
        if (count == 1) {
            printf("This is going to be root node \n");
            scanf("%d", &n);
            root = cnode(n);
            count--;
            priv = root;
        }        //ending if
        else {
            printf("Enter the number of siblings to this node\n");
            scanf("%d", &sib);
            while (sib > 0) {
                printf
                    ("Enter direction you want to go LEFT 1 RIGHT 2 TOP 3 DOWN 4\n");
                scanf("%d", &dir);
                printf("Enter the data  for graph node\n");
                scanf("%d", &n);
                temp = cnode(n);
                if (dir == 1) {
                    priv->LEFT = temp;
                }
                if (dir == 2) {
                    priv->RIGHT = temp;
                }
                if (dir == 3) {
                    priv->TOP = temp;
                }
                if (dir == 4) {
                    priv->DOWN = temp;
                }
                sib--;
            }    //ending while of sibling
            priv = temp;    //priv is equal to which temp?
        }        //ending else
        [B]printf
            ("Enter 1 to continue adding nodes to graph any thing else would take you out\n");[/B]
        scanf("%d", &choice);
    }            //ending while
}                //ending main

graph cnode(int data)
{
    graph temp = (graph) malloc(sizeof(graph));

    temp->data = data;
    temp->LEFT = NULL;
    temp->RIGHT = NULL;
    temp->TOP = NULL;
    temp->DOWN = NULL;
    temp->color = -1;
    return temp;
}

qnode travel_graph(graph rh)
{
    qnode qt;
    if (rh->LEFT) {
        qt = cque(rh);
    }
    if (rh->RIGHT) {
        qt = cque(rh);
    }
    if (rh->TOP) {
        qt = cque(rh);
    }
    if (rh->DOWN) {
        qt = cque(rh);
    }
    return qt;
}

```

I want to achieve the style as the guy [here]("http://stackoverflow.com/questions/3905238/opening-curly-bracket-brace-position-on-code/4527333#4527333") has discussed.But in my case when I try 
indent -linux graph.c
You can see the printf statement which I highlighted has broken to next line.
I do not want this to happen so what should I use from indent's man page.

I don't use 'indent' - I indent already in the editor. But one thing you can do with long strings like this that make it impossible to fit even a part of the statement on one line, is to take apart the string:

```
                printf("Enter direction you want to go "
                       "LEFT 1 RIGHT 2 TOP 3 DOWN 4\n");

```

---

