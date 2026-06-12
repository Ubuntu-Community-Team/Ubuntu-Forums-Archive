---
title: "Insert an element after a specific item."
date: 2010-05-02
forum: Programming Talk
---

### Post by zhenya1 on 2010-05-02
[SIZE=3]how to create a function that would be able to insert an element after a specific item.
Here's my list:[/SIZE]
[SIZE=3][/SIZE] 
[FONT=monospace][COLOR=#0000ff]```
 [FONT=monospace][COLOR=#0000ff]struct[/COLOR] list[COLOR=#008000]{[/COLOR]
[COLOR=#0000ff]char[/COLOR] c[COLOR=#008080];[/COLOR]
list [COLOR=#000040]*[/COLOR]next[COLOR=#008080];[/COLOR]
[COLOR=#008000]}[/COLOR][COLOR=#000040]*[/COLOR]p,[COLOR=#000040]*[/COLOR]cur,[COLOR=#000040]*[/COLOR]prev,[COLOR=#000040]*[/COLOR]top[COLOR=#008080];[/COLOR]

[COLOR=#0000ff]void[/COLOR] show[COLOR=#008000]([/COLOR][COLOR=#0000ff]void[/COLOR][COLOR=#008000])[/COLOR][COLOR=#008080];[/COLOR]
[COLOR=#0000ff]void[/COLOR] push[COLOR=#008000]([/COLOR][COLOR=#0000ff]char[/COLOR] value[COLOR=#008000])[/COLOR][COLOR=#008080];[/COLOR]
[COLOR=#0000ff]void[/COLOR] pop[COLOR=#008000]([/COLOR][COLOR=#0000ff]char[/COLOR] value[COLOR=#008000])[/COLOR][COLOR=#008080];[/COLOR]

[COLOR=#0000ff]int[/COLOR] main[COLOR=#008000]([/COLOR][COLOR=#008000])[/COLOR]
[COLOR=#008000]{[/COLOR]
    top[COLOR=#000080]=[/COLOR][COLOR=#0000dd]0[/COLOR][COLOR=#008080];[/COLOR]
    [COLOR=#0000ff]char[/COLOR] key,value[COLOR=#008080];[/COLOR]
    [COLOR=#0000ff]int[/COLOR] done[COLOR=#000080]=[/COLOR][COLOR=#0000ff]false[/COLOR][COLOR=#008080];[/COLOR]
    [COLOR=#0000ff]while[/COLOR][COLOR=#008000]([/COLOR][COLOR=#000040]![/COLOR]done[COLOR=#008000])[/COLOR][COLOR=#008000]{[/COLOR]
        [COLOR=#0000dd]system[/COLOR][COLOR=#008000]([/COLOR][COLOR=#ff0000]"cls"[/COLOR][COLOR=#008000])[/COLOR][COLOR=#008080];[/COLOR]
        show[COLOR=#008000]([/COLOR][COLOR=#008000])[/COLOR][COLOR=#008080];[/COLOR]
        [COLOR=#0000dd]printf[/COLOR][COLOR=#008000]([/COLOR][COLOR=#ff0000]"[COLOR=#000099]**\n**[/COLOR]A)dd[COLOR=#000099]**\n**[/COLOR]D)elete[COLOR=#000099]**\n**[/COLOR]Q)uit[COLOR=#000099]**\n**[/COLOR]"[/COLOR][COLOR=#008000])[/COLOR][COLOR=#008080];[/COLOR]
        key[COLOR=#000080]=[/COLOR][COLOR=#0000dd]getchar[/COLOR][COLOR=#008000]([/COLOR][COLOR=#008000])[/COLOR][COLOR=#008080];[/COLOR]
        [COLOR=#0000ff]switch[/COLOR][COLOR=#008000]([/COLOR][COLOR=#0000dd]toupper[/COLOR][COLOR=#008000]([/COLOR]key[COLOR=#008000])[/COLOR][COLOR=#008000])[/COLOR]
        [COLOR=#008000]{[/COLOR]
        [COLOR=#0000ff]case[/COLOR] [COLOR=#ff0000]'A'[/COLOR][COLOR=#008080]:[/COLOR]
    value[COLOR=#000080]=[/COLOR]getch[COLOR=#008000]([/COLOR][COLOR=#008000])[/COLOR][COLOR=#008080];[/COLOR]
    push[COLOR=#008000]([/COLOR]value[COLOR=#008000])[/COLOR][COLOR=#008080];[/COLOR]
    [COLOR=#0000ff]break[/COLOR][COLOR=#008080];[/COLOR]
        [COLOR=#0000ff]case[/COLOR] [COLOR=#ff0000]'D'[/COLOR][COLOR=#008080]:[/COLOR]
            [COLOR=#0000dd]printf[/COLOR][COLOR=#008000]([/COLOR][COLOR=#ff0000]"[COLOR=#000099]**\n**[/COLOR]Del:[COLOR=#000099]**\n**[/COLOR]"[/COLOR][COLOR=#008000])[/COLOR][COLOR=#008080];[/COLOR]
            value[COLOR=#000080]=[/COLOR]getch[COLOR=#008000]([/COLOR][COLOR=#008000])[/COLOR][COLOR=#008080];[/COLOR]
            pop[COLOR=#008000]([/COLOR]value[COLOR=#008000])[/COLOR][COLOR=#008080];[/COLOR]
            [COLOR=#0000ff]break[/COLOR][COLOR=#008080];[/COLOR]
        [COLOR=#0000ff]case[/COLOR] [COLOR=#ff0000]'Q'[/COLOR][COLOR=#008080]:[/COLOR]
            done[COLOR=#000080]=[/COLOR][COLOR=#0000ff]true[/COLOR][COLOR=#008080];[/COLOR]
            [COLOR=#0000ff]break[/COLOR][COLOR=#008080];[/COLOR]
        [COLOR=#008000]}[/COLOR]
    [COLOR=#008000]}[/COLOR]
    [COLOR=#0000ff]return[/COLOR] [COLOR=#0000dd]0[/COLOR][COLOR=#008080];[/COLOR]
[COLOR=#008000]}[/COLOR]
[COLOR=#0000ff]void[/COLOR] push[COLOR=#008000]([/COLOR][COLOR=#0000ff]char[/COLOR] value[COLOR=#008000])[/COLOR]
[COLOR=#008000]{[/COLOR]
    [COLOR=#0000dd]printf[/COLOR][COLOR=#008000]([/COLOR][COLOR=#ff0000]"[COLOR=#000099]**\n**[/COLOR]Input:[COLOR=#000099]**\n**[/COLOR]"[/COLOR][COLOR=#008000])[/COLOR][COLOR=#008080];[/COLOR]
    p[COLOR=#000080]=[/COLOR][COLOR=#0000dd]new[/COLOR] list[COLOR=#008080];[/COLOR]
    p[COLOR=#000040]-[/COLOR][COLOR=#000080]>[/COLOR]c[COLOR=#000080]=[/COLOR]value[COLOR=#008080];[/COLOR]
    p[COLOR=#000040]-[/COLOR][COLOR=#000080]>[/COLOR]next[COLOR=#000080]=[/COLOR][COLOR=#0000ff]NULL[/COLOR][COLOR=#008080];[/COLOR]
    [COLOR=#0000ff]while[/COLOR][COLOR=#008000]([/COLOR]cur [COLOR=#000040]&&[/COLOR] p[COLOR=#000040]-[/COLOR][COLOR=#000080]>[/COLOR]c [COLOR=#000080]>[/COLOR] cur[COLOR=#000040]-[/COLOR][COLOR=#000080]>[/COLOR]c[COLOR=#008000])[/COLOR]
    [COLOR=#008000]{[/COLOR]
    prev[COLOR=#000080]=[/COLOR]cur[COLOR=#008080];[/COLOR]
    cur[COLOR=#000080]=[/COLOR]cur[COLOR=#000040]-[/COLOR][COLOR=#000080]>[/COLOR]next[COLOR=#008080];[/COLOR]
    [COLOR=#008000]}[/COLOR]
    [COLOR=#0000ff]if[/COLOR][COLOR=#008000]([/COLOR]prev[COLOR=#000080]==[/COLOR][COLOR=#0000ff]NULL[/COLOR][COLOR=#008000])[/COLOR]
    [COLOR=#008000]{[/COLOR]
    p[COLOR=#000040]-[/COLOR][COLOR=#000080]>[/COLOR]next[COLOR=#000080]=[/COLOR]top[COLOR=#008080];[/COLOR]
    top[COLOR=#000080]=[/COLOR]p[COLOR=#008080];[/COLOR]
    [COLOR=#008000]}[/COLOR]
    [COLOR=#0000ff]else[/COLOR]
    [COLOR=#008000]{[/COLOR]
    p[COLOR=#000040]-[/COLOR][COLOR=#000080]>[/COLOR]next[COLOR=#000080]=[/COLOR]cur[COLOR=#008080];[/COLOR]
    prev[COLOR=#000040]-[/COLOR][COLOR=#000080]>[/COLOR]next[COLOR=#000080]=[/COLOR]p[COLOR=#008080];[/COLOR]
    [COLOR=#008000]}[/COLOR]
[COLOR=#008000]}[/COLOR]
[COLOR=#0000ff]void[/COLOR] pop[COLOR=#008000]([/COLOR][COLOR=#0000ff]char[/COLOR] value[COLOR=#008000])[/COLOR]
[COLOR=#008000]{[/COLOR]
    prev[COLOR=#000080]=[/COLOR]top[COLOR=#008080];[/COLOR]cur[COLOR=#000080]=[/COLOR]top[COLOR=#000040]-[/COLOR][COLOR=#000080]>[/COLOR]next[COLOR=#008080];[/COLOR]
    [COLOR=#0000ff]if[/COLOR][COLOR=#008000]([/COLOR]value[COLOR=#000080]==[/COLOR]top[COLOR=#000040]-[/COLOR][COLOR=#000080]>[/COLOR]c[COLOR=#008000])[/COLOR]
    [COLOR=#008000]{[/COLOR]
    p[COLOR=#000080]=[/COLOR]top[COLOR=#008080];[/COLOR]
    top[COLOR=#000080]=[/COLOR]top[COLOR=#000040]-[/COLOR][COLOR=#000080]>[/COLOR]next[COLOR=#008080];[/COLOR]
    [COLOR=#0000dd]free[/COLOR] [COLOR=#008000]([/COLOR]p[COLOR=#008000])[/COLOR][COLOR=#008080];[/COLOR]
    [COLOR=#008000]}[/COLOR]
    [COLOR=#0000ff]else[/COLOR]
    [COLOR=#008000]{[/COLOR]
    [COLOR=#0000ff]while[/COLOR][COLOR=#008000]([/COLOR]cur[COLOR=#000040]![/COLOR][COLOR=#000080]=[/COLOR][COLOR=#0000ff]NULL[/COLOR] [COLOR=#000040]&&[/COLOR] value[COLOR=#000040]![/COLOR][COLOR=#000080]=[/COLOR]cur[COLOR=#000040]-[/COLOR][COLOR=#000080]>[/COLOR]c[COLOR=#008000])[/COLOR]
    [COLOR=#008000]{[/COLOR]
    prev[COLOR=#000080]=[/COLOR]cur[COLOR=#008080];[/COLOR]
    cur[COLOR=#000080]=[/COLOR]cur[COLOR=#000040]-[/COLOR][COLOR=#000080]>[/COLOR]next[COLOR=#008080];[/COLOR]
    [COLOR=#008000]}[/COLOR]
    [COLOR=#0000ff]if[/COLOR][COLOR=#008000]([/COLOR]cur[COLOR=#000040]![/COLOR][COLOR=#000080]=[/COLOR][COLOR=#0000dd]0[/COLOR][COLOR=#008000])[/COLOR]
    [COLOR=#008000]{[/COLOR]
    p[COLOR=#000080]=[/COLOR]cur[COLOR=#008080];[/COLOR]
    prev[COLOR=#000040]-[/COLOR][COLOR=#000080]>[/COLOR]next[COLOR=#000080]=[/COLOR]cur[COLOR=#000040]-[/COLOR][COLOR=#000080]>[/COLOR]next[COLOR=#008080];[/COLOR]
    [COLOR=#0000dd]free[/COLOR] [COLOR=#008000]([/COLOR]p[COLOR=#008000])[/COLOR][COLOR=#008080];[/COLOR]
    [COLOR=#008000]}[/COLOR]
         [COLOR=#008000]}[/COLOR]
[COLOR=#008000]}[/COLOR]
[COLOR=#0000ff]void[/COLOR] show[COLOR=#008000]([/COLOR][COLOR=#008000])[/COLOR]
[COLOR=#008000]{[/COLOR]
    p[COLOR=#000080]=[/COLOR]top[COLOR=#008080];[/COLOR]
    [COLOR=#0000ff]if[/COLOR][COLOR=#008000]([/COLOR]p[COLOR=#000080]==[/COLOR][COLOR=#0000dd]0[/COLOR][COLOR=#008000])[/COLOR]
    [COLOR=#0000dd]printf[/COLOR][COLOR=#008000]([/COLOR][COLOR=#ff0000]"[COLOR=#000099]**\n**[/COLOR] list is empty[COLOR=#000099]**\n**[/COLOR]"[/COLOR][COLOR=#008000])[/COLOR][COLOR=#008080];[/COLOR]
    [COLOR=#0000ff]else[/COLOR]
    [COLOR=#0000dd]printf[/COLOR][COLOR=#008000]([/COLOR][COLOR=#ff0000]"[COLOR=#000099]**\n**[/COLOR]LIST:[COLOR=#000099]**\n**[/COLOR]"[/COLOR][COLOR=#008000])[/COLOR][COLOR=#008080];[/COLOR]
    [COLOR=#0000ff]while[/COLOR][COLOR=#008000]([/COLOR]p[COLOR=#008000])[/COLOR]
    [COLOR=#008000]{[/COLOR]
    [COLOR=#0000dd]printf[/COLOR][COLOR=#008000]([/COLOR][COLOR=#ff0000]"%c[COLOR=#000099]**\n**[/COLOR]"[/COLOR],p[COLOR=#000040]-[/COLOR][COLOR=#000080]>[/COLOR]c[COLOR=#008000])[/COLOR][COLOR=#008080];[/COLOR]
    p[COLOR=#000080]=[/COLOR]p[COLOR=#000040]-[/COLOR][COLOR=#000080]>[/COLOR]next[COLOR=#008080];[/COLOR]
    [COLOR=#008000]}[/COLOR]
[COLOR=#008000]}[/COLOR][/FONT]

```[/COLOR][/FONT]

---

### Post by MadCow108 on 2010-05-02
seems like homework.
homework questions are not allowed.

If you wrote the push and pop functions it should not take much thought to figure out the insert by yourself.

---

### Post by zhenya1 on 2010-05-02
> **MadCow108 said:**
> seems like homework.
homework questions are not allowed.
 
If you wrote the push and pop functions it should not take much thought to figure out the insert by yourself.
 
[SIZE=2]There is an attempt, but it does not work :( 
[/SIZE][COLOR=blue][FONT=Courier New]void[/FONT][/COLOR][FONT=Courier New] add([COLOR=blue]char[/COLOR] value)[/FONT]
[FONT=Courier New]{[/FONT]
[FONT=Courier New]      p=[COLOR=blue]new[/COLOR] list;[/FONT]
[FONT=Courier New]      [COLOR=blue]if[/COLOR](p==NULL) { printf([COLOR=#a31515]"Error"[/COLOR]);getch();exit(1);}[/FONT]
[FONT=Courier New]      p->c=value;[/FONT]
[FONT=Courier New]      p->next=NULL;[/FONT]
[FONT=Courier New]top=prev;[/FONT]
[COLOR=blue][FONT=Courier New]for[/FONT][/COLOR][FONT=Courier New]([COLOR=blue]int[/COLOR] i=0;top!=NULL;i++)[/FONT]
[FONT=Courier New]{[/FONT]
[FONT=Courier New]      [COLOR=blue]if[/COLOR](i==value)[/FONT]
[FONT=Courier New]      {[/FONT]
[FONT=Courier New]            p->next=top->next;[/FONT]
[FONT=Courier New]      }[/FONT]
[FONT=Courier New]      top->next=p; [COLOR=blue]break[/COLOR];[/FONT]
[FONT=Courier New]}[/FONT]
[FONT=Courier New]top=top->next;[/FONT]
[FONT=Courier New]}[/FONT]

---

### Post by LKjell on 2010-05-02
Well this looks like a linked list so if you mean after I assume after the order of the element.

What you do is you need to know the pointer to the struct to the specific item. How you do that is up to you. Then you make a temp pointer to hold the next item of list. Create what you are going to insert. If you already have that pointer it is good. Now you point the next pointer in the specific item to the inserted one. From the inserted next pointer you point it to the next pointer you point to the temp pointer.

So if you have a list like this:

a -> b -> c -> d

And want to insert e between b and c you have

temp = c;
b.next = e;
e.next = temp;

---

