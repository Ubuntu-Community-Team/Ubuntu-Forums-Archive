---
title: "Can anyone suggest best IDE for python3 on Ubuntu Desktop 15.04 LTS?"
date: 2015-10-14
forum: Programming Talk
---

### Post by Tushar_Niras on 2015-10-14
Hi Team,

can anyone please suggest IDE for python development on Ubuntu Desktop. Anyone who used.. please suggest.

Regards,

TUSHAR NIRAS

---

### Post by Bucky Ball on 2015-10-14
*Thread moved to **Programming Talk**.*

You might have better luck here.

---

### Post by mystics on 2015-10-14
You don't really need to use a full IDE. A good programming-focused text editor and terminal will do just fine. That said, here are a few programs you may want to try out.

**Sublime Text:** This is the one I probably see used most often. It's been a while since I used it personally, but from what I remember, it was a nice looking, fast text editor that had good customization options. It also could offer things like code completion, auto-indentation, multi-line editing, and other helpful features to Python. I also hear that the community has put together a strong list of snippets, but I haven't personally used them.

If you want to try it, the top response on this page shows how to do it with apt-get along with a few other methods: [http://askubuntu.com/questions/172698/how-do-i-install-sublime-text-2-3](http://askubuntu.com/questions/172698/how-do-i-install-sublime-text-2-3)

**IDLE:** I haven't personally used it, but it is the one I see most referenced in Python books, mostly because it is sort of the official IDE for Python. You can find it by searching either the Ubuntu Software Center or Synaptic Package Manager.

**Visual Studio Code:** Code is basically what happens if you push elements of Github's Atom, Sublime Text, and elements of Visual Studio together. Like Sublime Text, it offers a lot of useful features for Python like auto-indentation. I know it has support for snippets as well, but there doesn't seem to yet be a community offering to make ones to add in bulk, so you'll have to write them all yourself. Overall, though, it is a very solid text editor and the one I've been using the most recently.

You can either install it from the official website or through Ubuntu Make. Just type into a terminal:

```

sudo add-apt-repository ppa:ubuntu-desktop/ubuntu-make
sudo apt-get update
sudo apt-get install ubuntu-make
umake web visual-studio-code

```

---

