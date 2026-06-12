---
title: "my tree cant delete its children"
date: 2008-12-06
forum: Packaging and Compiling Programs
---

### Post by thebinaryblob on 2008-12-06
I was making a tree, but when I ran it, it would not delete its children (I started out by trying to make it able to correctly delete its children)
I made a small program that demonstrates this, when I run it, it does not crash, despite the extra delete of the third node

```
#include <iostream>

/////////////////////////////////////////////////////////

class Node {
	Node* child;
	
	public:
		Node(Node* setChild = NULL);
		~Node();
};

Node::Node(Node* setChild) {
	child = setChild;
}

Node::~Node() {
	if(child != NULL) {delete child;}
}

///////////////////////////////////////////////////////

int main() {
	Node *first, *second, *third;
	
	third = new Node();
	second= new Node(third);
	first = new Node(second);
	
	delete first;
	delete third; //this should crash it
	
	return 0;
}
```

---

