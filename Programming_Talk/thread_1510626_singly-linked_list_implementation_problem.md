---
title: "singly-linked list implementation problem"
date: 2010-06-15
forum: Programming Talk
---

### Post by bellereve on 2010-06-15
Hi, I'm trying to implement a singly-linked list, and when I test my program, it comes out with weird characters instead of the char that I'm inserting in the list. I'm thinking it's a reference problem, but I'm not sure how to fix it...Here are parts of the code...

  template <typename T>
  class SLL {
  
private:
    struct Node {
        T data;
        Node *next;
    }; 
    Node head;
    int t_size;

public:
    SLL() {
        head.next = NULL;
	t_size = 0;
    }

    void insert( const T& element, int position ) {
        if (head.next == NULL){
            Node NEW;
            NEW.data = element;
            head.next = &NEW;
            NEW.next = NULL;
        }
        else {
            Node *TEMP;
            TEMP = head.next;
 
           if (position == 0){
                Node NEW;
                NEW.data = element;
                head.next = &NEW;
                NEW.next = TEMP;
            }
	    else{
              for (int i=0; i <= position; i++){
                  if (i == position-1){
			Node n;
			n.data = element;
			n.next = TEMP->next->next;
			TEMP->next = &n;
                  }
                  else {
                      TEMP = TEMP -> next;
                 }
              }
           }
        }
	t_size++;
    }

  std::ostream& print( std::ostream& out ) const {
	int x = 1;        
	if (head.next == NULL){
            out << "<empty list>";
        }
	else{ 
		Node *TEMP = head.next;
		out << "[ ";
		out << TEMP->data;
		while(x < size()){
			out << " , ";
			out << TEMP->data;
			TEMP = TEMP->next;
			x++;
		}
	out << " ]" << endl;
	}
    }

    friend std::ostream& operator<<(std::ostream& out, SLL& list){
        return list.print(out);
    }

---

### Post by dwhitney67 on 2010-06-15
You need to allocate your Nodes.  Simply declaring them as local variables (on the stack) ain't going to cut it.  As soon as your insert() method returns, your Node variable 'NEW' is history.

A little word of advice...

1.  Avoid meaningless acronyms for class or variable names (eg. SLL)
2.  Avoid using reserved words for class or variable names (eg. NEW)
3.  For now, keep things simple and insert new Nodes either at the front or the end of the list.

P.S.  I would define SLL::head to be a pointer.  The first item you insert should be made the head; afterwards, each subsequent call to insert() should insert either in front of head or to its next pointer.

P.S. #2  Use [ CODE ] tags when posting code.

---

### Post by Some Penguin on 2010-06-15
1-  Please use [PHP]```

```[/PHP]  tags.

2- When printing... f you're iterating through a list anyway, you can check the 'next' pointer instead of comparing against a size field.

3- Your insert() routine is broken, because your 'next' pointers are pointing to local variables that go away as soon as you return from the function.  Basically, your nodes are co-located with the call stack.  This is the cause of what you're seeing.


You'll want to use either 'new' or 'malloc'.  new would be more C++-ish.  You'll then want to use delete / free.

---

### Post by trent.josephsen on 2010-06-15
You also don't return anything in your print() method.  The -Wall switch to g++ will tell you this.  It's always a good idea to enable compiler warnings because they catch simple mistakes like this that can be hard to track down otherwise.

---

