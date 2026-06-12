---
title: "Question about Anjuta and void main(){}"
date: 2007-07-27
forum: Programming Talk
---

### Post by CryptiniteDemon on 2007-07-27
I've been trying to adjust to ubuntu for a while now and I've finally come to the point where I want to switch from Visual Studio.net  to Anjuta.  But one thing that's really irritating is that anjuta does not let me write any code that has a void main function.

It insists that it be an int.  In visual studio I made all my main functions void cause I didn't like the 1 showing up at the beginning of my programs.

So is this just some BS sloopy thing that visual studio lets us get away with or is it something with Anjuta.  If so, none of my C++ profs ever said that main had to be type int.

---

### Post by Wybiral on 2007-07-27
> **CryptiniteDemon said:**
> I've been trying to adjust to ubuntu for a while now and I've finally come to the point where I want to switch from Visual Studio.net  to Anjuta.  But one thing that's really irritating is that anjuta does not let me write any code that has a void main function.

It insists that it be an int.  In visual studio I made all my main functions void cause I didn't like the 1 showing up at the beginning of my programs.

So is this just some BS sloopy thing that visual studio lets us get away with or is it something with Anjuta.  If so, none of my C++ profs ever said that main had to be type int.

It is standard for main to be of type int.

It should always return something from your program (preferably a 0 for success).

Just be safe and use the typical "int main()" instead of "void main()" even if you don't plan to return anything.

---

### Post by Paul820 on 2007-07-27
main must always return an int, here's a link to explain [http://www.research.att.com/~bs/bs_faq2.html#void-main]("http://www.research.att.com/~bs/bs_faq2.html#void-main")

---

### Post by CryptiniteDemon on 2007-07-27
Thanks guys.  That kinda pisses me off.  I've been through 3 c++ professors and none of them told us about it needing to be int.  All they said was that it was good to use it cause it shows you that your program terminated successfully.  They never said it was ISO standard to do so.

---

