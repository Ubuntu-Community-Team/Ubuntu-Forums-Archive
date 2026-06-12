---
title: "Pastebin access from terminal"
date: 2009-08-02
forum: Programming Talk
---

### Post by ideamonk on 2009-08-02
Hi,

I've written a useful python script that helps you paste your code over various paste-bins directly from a terminal. 
Its as simple as this -

```
$ pypaste myfoobar.rb
http://paste.ubuntu.com/######
$
```

snapshot - [*here*]("http://2.bp.blogspot.com/_Jg5VhRmvVtY/SnYACI1h8eI/AAAAAAAAAqU/DZQaJiyTP7A/s1600-h/Screenshot-2.png")

I've written more about it here - [http://ideamonk.blogspot.com/2009/08/pypaste-pastebins-at-your-terminal.html](http://ideamonk.blogspot.com/2009/08/pypaste-pastebins-at-your-terminal.html)

The project is available on github - [http://github.com/ideamonk/pypaste/tree/master](http://github.com/ideamonk/pypaste/tree/master)

It's pretty easy to install.

Hope this helps you speed up your work. I have tried to make the source easy to understand and hackable, I would like to know if someone would be interested in extending it over more pastebin services.

Note: I just learnt that there is something called pastebinit which is very popular. Sad that i didn't know about it before i started. The good part is PyPaste automatically detects syntax highlighting for you.

Have a great time.

---

### Post by .Maleficus. on 2009-08-02
This looks very cool, thanks for sharing.  I personally don't have an use for it but I'm sure somebody here will find it useful.  If I may make a suggestion though; I took a look at the install.sh file, and noticed that your installer assumes that Bash is the shell in use on the system.  As a Zsh user, this doesn't work well for me :).  Of course I could go in and change it to my .zshrc, but if you used the $SHELL variable to find the default shell your users wouldn't need to go through that step.  Otherwise, great job.

---

### Post by Can+~ on 2009-08-02
Nice.

Also, gnome-do has a similar feature, in which you can send selected text directly to paste bin.

(Image: [http://img.photobucket.com/albums/v517/CanXp/sendtopbin.png](http://img.photobucket.com/albums/v517/CanXp/sendtopbin.png))

*edit:
You could also add that it sends firefox to that link, with the [webbrowser]("http://docs.python.org/library/webbrowser.html#webbrowser.open_new_tab") module is pretty easy ([FONT="Courier New"]webbrowser.open_new_tab(url)[/FONT]).

---

### Post by ideamonk on 2009-08-16
Woah! the gnome do stuff is pretty cool. I'm not aware of zsh, will look into implementing $SHELL stuff soon.

---

