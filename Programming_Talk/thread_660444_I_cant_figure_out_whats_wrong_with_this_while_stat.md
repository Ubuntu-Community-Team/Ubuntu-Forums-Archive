---
title: "I cant figure out whats wrong with this while statement"
date: 2008-01-06
forum: Programming Talk
---

### Post by speedingbullet on 2008-01-06
```

int main()
{
   int attack;
   int hp = 7;   

while (hp > 0  && --hp)
{
cout <<"ATTACK!\n";
cout <<"but what do you choose?\n";
cin >> attack;
cout << "your opponent still has " << hp <<" hp\n";
}

return 0;

} 

```

I am trying to design a simple combat system so I'll know how to make one... but I can't seem to get it right. No matter what I enter in the program, the program for some reason thinks its always a 1:

ATTACK!
but what do you choose?
1
your opponent still has 6 hp
ATTACK!
but what do you choose?
2
your opponent still has 5 hp
ATTACK!
but what do you choose?
3
your opponent still has 4 hp
ATTACK!
but what do you choose?
4
your opponent still has 3 hp
ATTACK!
but what do you choose?
5
your opponent still has 2 hp
ATTACK!
but what do you choose?


the strange thing is, It was working earlier, but then when I started adding on to it, it didn't work anymore, so I undid a lot of changes until it was in its original form which you see now, but It still didn't work anymore... what on earth am I doing wrong?

---

### Post by Acglaphotis on 2008-01-06
[PHP]#include <cstdio>
#include <cstdlib>
#include <iostream>
using namespace std;
int main()
{
       int attack;
       int hp = 7;

          while (hp > 0)
          {
              cout <<"ATTACK!\n";
              cout <<"but what do you choose?\n";
              cin >> attack;
              hp -= attack;
              cout << "your opponent still has " << hp <<" hp\n";
          }

          return 0;

}
[/PHP]

There, fixed.

The problem was than you only did a --hp but you didn't substract attack from hp.

---

### Post by dwhitney67 on 2008-01-06
Nothing; it works fine for me.  Your code snippet does however lack the '#include <iostream>' and the 'using namespace std;' statement.

---

### Post by speedingbullet on 2008-01-06
THANK YOU BOTH!

I was just experimenting to see how I could get this to work.. I had no idea that you could use -=.... now I do, thanks!

---

