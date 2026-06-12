---
title: "[C++] Struct in class"
date: 2009-03-27
forum: Programming Talk
---

### Post by kjohansen on 2009-03-27
I have the below in my header file:

[php]
struct Node
{
    double a;
    double * weights; //incoming weights
    double * weights_change_lag; //for momentum
    double bias_weight;
    double bias_weight_change_lag; //for momentum
    double delta;
    double in;
};

struct Layer
{
    int num_nodes;
    Node * nodes;
};

class NeuralNetwork
{
//some prototypes
}
[/php]

Is there a convention for where the structs should go?

Should the structs be where they are or should they go inside the class definition?

These structs could be private, they do not need to be used outside of the implementation.

---

### Post by maddog39 on 2009-03-27
You can do it either way. The compiler treats structures as classes with public as the default. So you can either be inside the class as private or protected sub classes or you can leave them the way they are. Use the method that makes the most sense for you application.

---

### Post by dwhitney67 on 2009-03-27
It is not uncommon to see nested classes/structs.  For example:

```

class LinkedList
{
  public:
    ...

  private:
    struct Node
    {
      int   data;
      Node* next;
    };

   Node* m_head;
};

```

---

