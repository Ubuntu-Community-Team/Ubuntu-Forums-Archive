---
title: "Some newbie C questions"
date: 2009-04-01
forum: Programming Talk
---

### Post by mvalviar on 2009-04-01
Hi all. I've been experimenting with C and I have a few questions. I ran programs (I compiled) that shows a a lot of output I goes seg fault. Then I tried to drain all available memory by looping malloc and it never seg faulted. I just said Killed. I was waiting for malloc to return NULL and say "Out of memory" but it never did. Could anyone explain this?

thanks

---

### Post by hessiess on 2009-04-01
Can you post your source code?

---

### Post by mvalviar on 2009-04-01
Sure here it is: ```
#include <assert.h>
#include <stdio.h>
#include <stdlib.h>
#include <time.h>

typedef struct Node {
	int d;
	struct Node* next;
} Node;

void split(Node *first, Node **left, Node **right)
{
	Node *runner = first;
	Node *skipper = first;
	Node *b4skipper = NULL;

	while (runner != NULL) {
		runner = runner->next;
		b4skipper = skipper;
		skipper = skipper->next;
		if (runner == NULL) break;
		runner = runner->next;
	}
	b4skipper->next = NULL;
	*left = first;
	*right = skipper;
}

void show(Node *np)
{
	if (np == NULL) {
		printf("NULL\n");
		return;
	}
	printf("%d->", np->d);
	show(np->next);
}

Node* merge(Node* left, Node* right)
{
	Node *head, *tail;

	if (left->d < right->d) {
		head = left;
		tail = left;
		left = left->next;
	} else {
		head = right;
		tail = right;
		right = right->next;
	}
	while (right != NULL && left != NULL) {
		if (left->d < right->d) {
			tail->next = left;
			tail = left;
			left = left->next;
		} else {
			tail->next = right;
			tail = right;
			right = right->next;
		}
	}
	if (left == NULL) tail->next = right;
	else tail->next = left;
	return head;
}

Node* mergesort(Node *head)
{
	Node *left, *right;
	if (head == NULL || head->next == NULL)
		return head;
	split(head, &left, &right);
	return merge(mergesort(left), mergesort(right));
}

int main(int argc, char *argv[])
{
	Node head, *tail, *to_add;
	int i, size;

	srand(time(NULL));
	head.next = NULL;
	tail = &head;
	if (argc == 1 || sscanf(argv[1], "%d", &size) == 0) size = 10;
	for (i = 0; i < size; i++) {
		if ((to_add = malloc(sizeof(Node))) == NULL) {
			fprintf(stderr, "Out of memory!\n");
			exit(EXIT_FAILURE);
		}
		to_add->d = rand() % 100;
		tail->next = to_add;
		to_add->next = NULL;
		tail = to_add;
	}
	printf("Unsorted: ");
	show(head.next);
	show(mergesort(head.next));
	printf("\n");
	return 0;
}
```

What I really wanted to know is how to make it exit gracefully if it has too.

---

### Post by kpatz on 2009-04-01
Your show function is calling itself recursively, which will max out the stack long before your mallocs run out of memory on the heap.

I rewrote your show function to use a while loop instead of recursion, as follows:

```

void show(Node *np)
{
        while(np)
        {
          printf("%d->", np->d);
          np = np->next;
        }
        printf("NULL\n");
}

```

and now your program will run successfully with larger size lists (I ran it successfully with 10 million).

As for your malloc loop experiment, the virtual memory manager in Linux will provide as much memory as your program asks for, but if the system runs out, the kernel may kill the offending process to keep the system from crashing, hence your "Killed".

The only time malloc() will return null is either the heap is corrupted or you're asking for a larger single chunk than the heap can handle (which is probably around 4 gigs in a 32-bit environment, lots more in a 64-bit).

If your program segfaults, it means you have a bug that needs to be fixed.

EDIT: I did find a way to make malloc fail (this is a handy way to test programs in limited-memory environments).  Use the command **ulimit -v (size in kilobytes)** to limit the maximum amount of virtual memory processes spawned by the shell can allocate.  Make sure to do it in a subshell (run sh or bash before running), since you can't raise the limit once you lower it unless you're root.  Exiting the subshell will take you back into a shell without the limit.

---

### Post by slavik on 2009-04-01
in the default configuration that is in ubuntu, the kernel will give you as much memory as you want, up to like 4TB or something. but even though you ask malloc for 1GB, it doesn't mean that you have the 1GB ready to use. the kernel only promises you 1GB, that 1GB has not yet been commited to your program. but once you start using that 1GB.

vm.overcommit_memory is the setting. put it into google for more info. :)

---

### Post by mvalviar on 2009-04-02
Very nice! Thanks! Damn I love doing c in GNU/Linux. I was experimenting with c under windows before but its utterly boring. 

I just thought the best way to run through the list is by recursion that why I wrote it that way.

---

