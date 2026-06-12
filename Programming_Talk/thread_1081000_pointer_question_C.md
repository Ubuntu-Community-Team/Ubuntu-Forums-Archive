---
title: "pointer question C"
date: 2009-02-26
forum: Programming Talk
---

### Post by pandaemonia on 2009-02-26
I have the code
```
Bool enqueue(Queue *AQueue, int processId, int arrivalTime, 
	     int serviceTime, int remainingTime) {
  Node *head;
  head = AQueue->head;
  Node *tail;
  tail = AQueue->tail;
  Node *tempnode;
  tempnode = (Node*)malloc(sizeof(Node));
  
  tempnode->processId = processId;
  tempnode->arrivalTime = arrivalTime;
  tempnode->serviceTime = serviceTime;
  tempnode->remainingTime = remainingTime;
  tempnode->next = NULL;
  
  if (tail == NULL){ 
    tail = tempnode;
    head = tempnode;
    } else {
	  (tail)->next = tempnode;
	  tail = tempnode;
	}
	return TRUE;
}
```.

The .h file is as follows:
```
typedef struct node{
  int processId;
  int arrivalTime;
  int serviceTime;
  int remainingTime;
  struct node *next; // points to the next node
} Node;


typedef struct queue{
  Node *head;
  Node *tail;
} Queue;
```

It's not actually adding anything to the queue. Why?

---

### Post by veda87 on 2009-02-26
> **pandaemonia said:**
> 
  tempnode = (Node*)malloc(sizeof(Node));

you have allocated memory for sizeof(Node) but Node is a pointer ... so it allocates only 4 bytes ...so it won,t work.... you have have allocate for entire struct node...

tempnode = (Node*)malloc(sizeof(struct node));

this will do ......hope you understand....

---

### Post by movieman on 2009-02-26
> **veda87 said:**
> you have allocated memory for sizeof(Node) but Node is a pointer ...

Node is a structure, so that should be fine.

The real problem is that the code only updates local variables, so the results of the update will disappear as soon as you return from the function call.

You need to update AQueue->head and AQueue-tail, not local copies of them.

---

