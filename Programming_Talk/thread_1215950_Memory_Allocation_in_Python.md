---
title: "Memory Allocation in Python"
date: 2009-07-17
forum: Programming Talk
---

### Post by Godd on 2009-07-17
I'm writing a program that multi-threads with two functions.

The first creates a list that once exceeds 10 items in length removes items until it is back down until it can add back in more items. (which is a bit cumbersome, and will need revision)

And the second outputs list[0] to stdout then removes the previously printed item.

The issue is that it seems to not free the memory used by the deleted items. And eventually peaks out on memory usage.
 
I was wondering how to allocate a set amount of memory to prevent this as it can never complete a cycle. Furthermore if such measures would solve the problem, and if not, what route would be fruitful.

---

### Post by Can+~ on 2009-07-17
> **Godd said:**
> I'm writing a program that multi-threads with two functions.

The first creates a list that once exceeds 10 items in length removes items until it is back down until it can add back in more items. (which is a bit cumbersome, and will need revision)

**And the second outputs list[0] to stdout then removes the previously printed item.**

The issue is that it seems to not free the memory used by the deleted items. And eventually peaks out on memory usage.
 
I was wondering how to allocate a set amount of memory to prevent this as it can never complete a cycle. Furthermore if such measures would solve the problem, and if not, what route would be fruitful.

Show some code; and use mylist.pop(0) to do **that**.

---

### Post by master_kernel on 2009-07-17
> **Can+~ said:**
> Show some code; and use mylist.pop(0) to do **that**.

IIRC, can't the del() function do the same thing? I need some touch-up work on my Python skills. :guitar:

---

### Post by Godd on 2009-07-17
As far as I can tell pop and del are relatively interchangeable, but pop relays back a message to stderr?

Correct me if I'm wrong.

---

### Post by Godd on 2009-07-17
[PHP]class generator(threading.Thread):

    def __init__(self):
        global iteration
        self.iteration  = []
        self.char_select = sys.argv[2] 
        self.iter_length = int(sys.argv[1])
        threading.Thread.__init__(self)

    def run(self):

        char_list = ['a','b','c','d','e','f','g','h','i','j','k','l','m','n','o','p','q','r','s','t','u','v','w','x','y','z']

        list_length = range(len(char_list))
        iter_length = generator.iter_length       

        global iteration
        generator.iteration
        global iteration
        iteration = generator.iterwords
        
        while iter_length != 9:                                #This is the main loop procedure
            if iter_length == 1:
                for x in list_length:
                    iteration.append(char_list[x])
                if len(iteration) >= 10:
                    del iteration[0]                                     #Sleep funtion prevents memory overflow
                iter_length = iter_length + 1
            if iter_length == 2:
                for x in list_length: 
                    for y in list_length:
                        iteration.append(char_list[x]+char_list[y])
                if len(iteration) >= 10:
                    del iteration[0]
                iter_length = iter_length + 1
            if iter_length == 3:
                for x in list_length:
                    for y in list_length:
                        for z in list_length:
                            iteration.append(char_list[x]+char_list[y]+char_list[z])
                if len(iteration) >= 10:
                    del iteration[0]
                iter_length = iter_length + 1
            if iter_length == 4:
                for x in list_length:
                    for y in list_length:
                        for z in list_length:
                            for w in list_length:
                                iteration.append(char_list[x]+char_list[y]+char_list[z]+char_list[w])
                if len(iteration) >= 10:
                    del iteration[0]
                iter_length = iter_length + 1
            if iter_length == 5:
                for x in list_length:
                    for y in list_length:
                        for z in list_length:
                            for w in list_length:
                                for q in list_length:
                                    iteration.append(char_list[x]+char_list[y]+char_list[z]+char_list[w]+char_list[q])
                if len(iteration) >= 10:
                    del iteration[0]
                iter_length = iter_length + 1
            if iter_length == 6:
                for x in list_length:
                    for y in list_length:
                        for z in list_length:
                            for w in list_length:
                                for q in list_length:
                                    for u in list_length:
                                        iteration.append(char_list[x]+char_list[y]+char_list[z]+char_list[w]+char_list[q]+char_list[u])
                if len(iteration) >= 10:
                    del iteration[0]
                iter_length = iter_length + 1
            if iter_length == 7:
                for x in list_length:
                    for y in list_length:
                        for z in list_length:
                            for w in list_length:
                                for q in list_length:
                                    for u in list_length:
                                        for e in list_length:
                                            iteration.append(char_list[x]+char_list[y]+char_list[z]+char_list[w]+char_list[q]+char_list[u]+char_list[e])
                if len(iteration) >= 10:
                    del iteration[0]
                iter_length = iter_length + 1
            if iter_length == 8:
                for x in list_length:
                    for y in list_length:
                        for z in list_length:
                            for w in list_length:
                                for q in list_length:
                                    for u in list_length:
                                        for e in list_length:
                                            for r in list_length:
                                                iteration.append(char_list[x]+char_list[y]+char_list[z]+char_list[w]+char_list[q]+char_list[u]+char_list[e]+char_list[r])
                if len(iteration) >= 10:
                    del iteration[0]
                iter_length = iter_length + 1
    print "I'm Done!"
[/PHP]

Thankyou Can+~. The problem was my list length checker never was never gotten to.

And Yes I know the script is ungodly. It's going to be re-written with Awk.

---

### Post by smartbei on 2009-07-18
The difference between list.pop(i) and del list[i] is that list.pop is a method that has a return value - the value of list[i] ight before the pop. del is a statement, and doesn't have a return value.

---

