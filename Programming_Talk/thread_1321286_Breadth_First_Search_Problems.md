---
title: "Breadth First Search Problems"
date: 2009-11-09
forum: Programming Talk
---

### Post by nebu on 2009-11-09
Can you tell me whats wrong with this BFS program with a adjacency list implementation o the graph...

i cant seem to find anything wrong

```

enum COLORS{WHITE,GRAY,BLACK};

typedef struct __q
{
    int key;
    struct __q *next;
}queue;

typedef struct __g
{
    int BFScount;
    int parent;
    int level;
    enum COLORS state;
    queue *adjacent;
}graph;

void enqueue(queue *q,int val)
{
    queue *tmp = (queue*)malloc(sizeof(queue));
    tmp->next = NULL;
    tmp->key = val;
    if(q==NULL)
    {
    q = tmp;
    return;
    }
    while(q->next!=NULL)
    q = q->next;
    q->next = tmp;
}

int dequeue(queue *q)
{
    queue *m = q;
    if(q==NULL)
    return;
    q = q->next;
    int val = m->key;
    free(m);
    return val;
}

void BFS(graph *g,int source,int n)
{
    int i;
    for(i=0;i<n;i++)
    {
    g[i].state = WHITE;
    g[i].parent = -1;
    g[i].level = INT_MAX;
    }
    g[source].state = GRAY;
    g[source].parent = source;
    g[source].level = 0;
    queue *q = NULL;
    enqueue(q,source);
    while(q!=NULL)
    {
    int u = dequeue(q);
    queue *v = g[u].adjacent;
    while(v!=NULL)
    {
        if(g[v->key].state == WHITE)
        {
        g[v->key].state = GRAY;
        g[v->key].level = g[u].level + 1;
        g[v->key].parent = u;
        enqueue(q,v->key);
        }
        v = v->next;
    }
    g[u].BFScount++;
    g[u].state = BLACK;
    }
}


```

---

### Post by mike_g on 2009-11-10
Perhaps a compliable program, or a little explanation would help. Do you get any errors? Or are you getting stuck in a loop?

---

