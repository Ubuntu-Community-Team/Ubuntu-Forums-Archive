---
title: "sorted circular list  algorithm"
date: 2009-01-03
forum: Programming Talk
---

### Post by babacan on 2009-01-03
Greetings
I am trying to implement a sorted insertion function to circular singly linked list at java but I am not able to acheive it, any help will be appreciated.

```

	void addElement(SingleNode input) {

//		if head is null
		if(head == null){
			head = input;
			head.next = head;
			return;
		}

		SingleNode current = head;
		SingleNode previous = null;

//		if not null
		do{

			if ( input.value <current.value ){

				if(previous == null){
					input.next = head;
					current.next= input;
					head = input;
					return;
				}

				else{
					previous.next = input;
					input.next = current;
					return;
				}
			}

			if(current.next == head){
				current.next = input;
				input.next = head;
				return;
			}

			previous = current;
			current = current.next;

		}
		while(current != head);

	}

```

---

### Post by dwhitney67 on 2009-01-03
Since your goal is to maintain a circular list, you need to keep track of the last node in the list; let's call this node 'tail'.

Initially your addElement() function incorrectly assumed that the node previous to the head was null.  It should be set equal to the tail.

There were other areas that also did not function as expected; hopefully I have corrected these.

Here's a partial listing of the code that I used to test with:
[php]
class LinkedList
{
  private SingleNode head;
  private SingleNode tail;

  ...

  public void addElement(SingleNode input)
  {
    if (head == null)
    {
      head = input;
      head.next = head;
      tail = head;
      return;
    }

    SingleNode current = head;
    SingleNode previous = tail;

    do
    {
      if (input.value < current.value)
      {
        previous.next = input;
        input.next = current;

        if (current == head)
        {
          head = input;
        }
        return;
      }

      if (current.next == head)    // of if (current == tail)
      {
        current.next = input;
        input.next = head;
        tail = input;
        return;
      }

      previous = current;
      current  = current.next;
    } while (current != head);
  }

  ...
}
[/php]

---

