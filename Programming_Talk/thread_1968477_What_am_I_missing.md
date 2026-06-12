---
title: "What am I missing?"
date: 2012-04-29
forum: Programming Talk
---

### Post by vanangamudi on 2012-04-29
Here is my problem. If I include gtkmm.h header everything is fine and the project compiles with no problem. but If I remove it, it shows the following error: [http://pastebin.com/0rpYpDPf](http://pastebin.com/0rpYpDPf)

I suspect that i was missing some headers, but the line "expected initializer before ‘<’ token" screws me up. help me


task.h
_____________________________________________________________
```
#ifndef _TASK_H_
#define _TASK_H_


#include<string.h>
#include<stdio.h>
#include<stdlib.h>
[COLOR="Red"]//#include<gtkmm.h>
[/COLOR]
class Task
{
    protected:
        int m_id;
        int m_priority;
        char m_task[64];

    public:
        //Task():m_id(0),m_priority(NORMAL),m_task(""){ }
        Task(int id, int pri, char* tsk){
            m_id = id ;
            m_priority = pri;
            strcpy(m_task,tsk);
        }

        int getID(){ return m_id; }
        int getPriority(){ return m_priority;  }
        char* getTaskString(){ return m_task;  }

        void dispTask()
        {
            printf("\n\t%d",m_id);
            printf("\t\t%d",m_priority);
            printf("\t\t%s",m_task);
        }

};


#endif //_TASK_H_

```
_____________________________________________________________

TodoList.h
_____________________________________________________________
```

#ifndef _TODOLIST_H_
#define _TODOLIST_H_

#include "task.h"

typedef std::list<Task> TaskList;


class TodoList{

    protected:
        TaskList m_todoList;

        void test();
    public:
        int Run();
        void addTask(Task tsk);

        void delTask(Task &tsk);
        void delTask(int id);

        void dispList();

};


#endif

```
_____________________________________________________________


TodoList.cpp
_____________________________________________________________
```
#include "TodoList.h"
#include<iostream>

void TodoList::addTask(Task tsk)
{
    m_todoList.push_back(tsk);
}

void TodoList::delTask(int id)
{

    TaskList::iterator elem;
    for(elem = m_todoList.begin(); elem != m_todoList.end();elem++){

        if(elem->getID() == id ){

            m_todoList.erase(elem);
            return;
        }

    }

}

void TodoList::dispList()
{
    TaskList::iterator elem;
    printf("\n\tID");
    printf("\t\tPriority");
    printf("\tTask");
    for(elem = m_todoList.begin(); elem != m_todoList.end();elem++){

        elem->dispTask();
    }

}

void TodoList::test()
{
    //Task tsk;

    for(int i=0;i<5;i++){

        Task tsk( i, i%3, " ");
        addTask(tsk);

    }
}

int TodoList::Run()
{
    test();

    int key=0,choice=0;
    int tmp;
    char tsk[32];
    Task *task;
    int count=0;

    while(key!=27){

        count++;
        printf("\n1.AddTask");
        printf("\n2.Delete Task");

        printf("\nEnter your Choice:\t");
        scanf("%d",&choice);

        switch(choice){

            case 1: printf("\nEnter the Task Priority:\t");
                    scanf("%d",&tmp);
                    printf("\nEnter the Description:\t");
                    std::cin >> tsk ;
                    task = new Task(count,tmp,tsk) ;
                    addTask(*task);
                    break;

            case 2: printf("\nEnter the Task ID:\t");
                    scanf("%d",&tmp);
                    delTask(tmp);
                    break;

            default: printf("\nerror: Enter a valid choice");
        }

        dispList();

        printf("\n\nPress any key to Continue or ESC to Quit");
        scanf("%d", &key);
    }

    return 0;
}

```
_____________________________________________________________

main.cc
_____________________________________________________________
```
#include "TodoList.h"


int main()
{
    TodoList list;
    list.Run();
}

```
_____________________________________________________________

---

### Post by dwhitney67 on 2012-04-29
Which will it be, C or C++?

If you have chosen C++, then the first thing I would recommend is that you include <list> within TodoList.h.

The second thing I would recommend would be to remove C-programming relics from C++ code; for instance, strcpy(), scanf(), printf(), and using char-arrays for strings.

---

### Post by vanangamudi on 2012-04-29
> **dwhitney67 said:**
> Which will it be, C or C++?

If you have chosen C++, then the first thing I would recommend is that you include <list> within TodoList.h.

The second thing I would recommend would be to remove C-programming relics from C++ code; for instance, strcpy(), scanf(), printf(), and using char-arrays for strings.

I'll try this. but it is supposed to work right. if include that gtkmm everything works fine...

---

### Post by dwhitney67 on 2012-04-29
> **vanangamudi said:**
> I'll try this. but it is supposed to work right. if include that gtkmm everything works fine...

I saw nothing in your code that is GTK-related; thus why are you concerned about including gtkmm?

As for the compiler error, it is indicated in the very first line that you posted to pastebin.

And btw, don't post errors or code to pastebin... post them here on this forum so that it can help others diagnose the issue.

---

