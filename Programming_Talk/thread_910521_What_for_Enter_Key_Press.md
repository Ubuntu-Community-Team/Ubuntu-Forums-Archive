---
title: "What for Enter Key Press"
date: 2008-09-04
forum: Programming Talk
---

### Post by DGortze380 on 2008-09-04
Hey all,

I blew through writing this program for class right up until this last problem. I can't get the damn thing to wait for the user to press the enter key.

example (not the actual program):
```


#include <iostream>
using namespace std;

int main()
{
     int x=0;

     while (true)
     {
          cout << x << endl
          x++;

          switch (x) //syntax for this switch example is probably off, didn't look it up.
          case 1:
                //some function call
                break;
          case 2:
                //some function call
                break;
          default:
                break;

          cout << "press enter to continue";

         // WTF will work here? I tried the following:
         
          // cin.ignore();
          // cin.get();
          // cin >> someVariable
          // getch();     //this one didn't work because I don't have the library and don't want to install it. Need an ANSI C solution
          // all of these do nothing, it just keeps looping.
          // cin >> someVariable works, but you have to type something and press enter. I just want to wait for 1 key stroke.
     }

return 0;
}


```

help.

---

### Post by DGortze380 on 2008-09-04
ok, here's a twist, cin.ignore() works in the code I just posted but not my actual source. Back to work, if i can't figure it out I'll post the source.

---

### Post by DGortze380 on 2008-09-04
I've got it working, but it's not really a clean solution. anyone that feels like looking at the source let me know I'll PM it to you.

---

### Post by LaRoza on 2008-09-04
getch is not standard. Use getchar() (C) or another input function.

---

### Post by jinksys on 2008-09-04
> **DGortze380 said:**
> I've got it working, but it's not really a clean solution. anyone that feels like looking at the source let me know I'll PM it to you.

You can't just post it here?

cin.get(); works for me.

---

### Post by DGortze380 on 2008-09-05
> **jinksys said:**
> You can't just post it here?

cin.get(); works for me.

I could, I try to avoid it because it's for a class, then it shows up in MOSS, I have to explain that it's not plagiarized, turns into a big thing.

I think the problem is that I'm using a switch statement in the loop. It work when I put cin.ignore() in each case and after the switch inside the loop. I'll edit the example in the first post to make it more clear.

---

