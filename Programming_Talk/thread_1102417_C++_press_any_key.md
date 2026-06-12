---
title: "C++ press any key"
date: 2009-03-21
forum: Programming Talk
---

### Post by celticbhoy on 2009-03-21
Just started learning C++, and I cant find an answer to <Press any key to coninue...>. I have googled and tried a couple of on line suggestions, but they just dont seem to work. What is the simple solution to this.

---

### Post by sisco311 on 2009-03-21
[thread]225713[/thread]
post #13

*Keyboard error: press any key to continue* :)

---

### Post by celticbhoy on 2009-03-21
Just tried it and it skips by it. Any other ideas?

---

### Post by Bölvaður on 2009-03-21
yes in the keyboard listener you could add a boolean variable that is used to check if you pressed a key or not, and before you write "press any key to continue..." you set that variable to false.

anykey = false;
cout<<"press any key..."<<endl;

while (!anykey)



well it really depends what you are doing... if you are doing cli you could just have cin... or some.. oh man Im not good with this :(

---

### Post by jimi_hendrix on 2009-03-21
getch(); //put at spot where you want it to pause

---

