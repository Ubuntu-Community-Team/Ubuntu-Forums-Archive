---
title: "Bash Scripting... Help?"
date: 2009-02-28
forum: Programming Talk
---

### Post by penguinpazazzer on 2009-02-28
Ok, this is my first post, so I apologize if it is in the wrong section.

Does anyone know of some sites that have FREE Shell Bash Scripting tutorials? I a visual effects major in college, and have an assignment to do, and I have no idea where to start. Most of the tutorials that I have found are really simple, and not very helpful.

I need a tutorial that does something, anything, as long as it's practical, and it MUST call on another application (Maya, Shake, an internet Browser, anything).

Thank you, thank you to anyone who can help me!

It is greatly appreciated.

---

### Post by amauk on 2009-02-28
bash scripts typically don't call out to GUI apps
(well, unless you're making a custom launcher for said app)
It's really a way of scripting terminal commands / CLI apps

There's no easy way to control GUI apps via a script, short of capturing keystrokes & X/Y mouse positions
which you really don't want to do...

But anyway, this is probably the best bash reference site
[http://tldp.org/LDP/abs/html/](http://tldp.org/LDP/abs/html/)

---

### Post by penguinpazazzer on 2009-03-01
> **amauk said:**
> bash scripts typically don't call out to GUI apps
(well, unless you're making a custom launcher for said app)
It's really a way of scripting terminal commands / CLI apps

There's no easy way to control GUI apps via a script, short of capturing keystrokes & X/Y mouse positions
which you really don't want to do...

But anyway, this is probably the best bash reference site
[http://tldp.org/LDP/abs/html/](http://tldp.org/LDP/abs/html/)

Thank you, that is quite helpful. I am still having trouble though, and I think I may not have made my question very clear. I need to launch another application. For instance, how would I create a code that opens Firefox, and automatically opens X number of tabs with different site URLs. Does that make sense?

Thank you so much for your help already. I really appreciate it.

---

### Post by jyaan on 2009-03-01
You would probably do better with Python. There are several libraries for doing GUI stuff, and making system calls is pretty easy, too. Check out the 'os' module. For opening a program with specific options, you will need to refer to the documentation on the command line arguments. For firefox, it is very easy. Just call it with each site as an argument, eg: ```
firefox site.com site2.com site3.com ... siteN.com
```

---

### Post by BoyOfDestiny on 2009-03-01
> **penguinpazazzer said:**
> Thank you, that is quite helpful. I am still having trouble though, and I think I may not have made my question very clear. I need to launch another application. For instance, how would I create a code that opens Firefox, and automatically opens X number of tabs with different site URLs. Does that make sense?

Thank you so much for your help already. I really appreciate it.

Yes bash can do that no problem.

The command would look like this

```
firefox www.google.com www.groklaw.net
```

That would open 2 tabs, with those respective sites, you can cut and paste it in terminal to test it out.

You can make scripts that rely on sequences of simple commands. Assuming the application you use takes command line parameters, skies the limit.

[http://linuxreviews.org/beginner/Bash-Scripting-Introduction-HOWTO/en/x67.html](http://linuxreviews.org/beginner/Bash-Scripting-Introduction-HOWTO/en/x67.html)

If you need some sort of gui with a bash script, try zenity (comes with Ubuntu as well)

[http://linux.byexamples.com/archives/259/a-complete-zenity-dialog-examples-1/](http://linux.byexamples.com/archives/259/a-complete-zenity-dialog-examples-1/)
[http://linux.byexamples.com/archives/265/a-complete-zenity-dialog-examples-2/](http://linux.byexamples.com/archives/265/a-complete-zenity-dialog-examples-2/)

---

### Post by penguinpazazzer on 2009-03-01
> **BoyOfDestiny said:**
> Yes bash can do that no problem.

The command would look like this

```
firefox www.google.com www.groklaw.net
```

That would open 2 tabs, with those respective sites, you can cut and paste it in terminal to test it out.

You can make scripts that rely on sequences of simple commands. Assuming the application you use takes command line parameters, skies the limit.

[http://linuxreviews.org/beginner/Bash-Scripting-Introduction-HOWTO/en/x67.html](http://linuxreviews.org/beginner/Bash-Scripting-Introduction-HOWTO/en/x67.html)

If you need some sort of gui with a bash script, try zenity (comes with Ubuntu as well)

[http://linux.byexamples.com/archives/259/a-complete-zenity-dialog-examples-1/](http://linux.byexamples.com/archives/259/a-complete-zenity-dialog-examples-1/)
[http://linux.byexamples.com/archives/265/a-complete-zenity-dialog-examples-2/](http://linux.byexamples.com/archives/265/a-complete-zenity-dialog-examples-2/)

Thank you! This is helping a LOT. One more question though. I am trying to do a simple pop-up box with radio buttons that select with website to launch, and then when you hit "OK", it launches the corresponding site. I am having trouble with it though, how can I attach a command to the $ans?

here is what I am trying to do... 

I'm not sure if I am using the if/then statement correctly. Can you give me further advice on this topic? Thanks again.

ans=$(zenity  --list  --text "Which site would you like to launch?" --radiolist  --column "Pick" --column "Site" TRUE "Digital Domain" FALSE "Industrial Light and Magic"); echo $ans

if [ $ans == "Digital Domain" ]; then
                firefox [www.digitaldomain.com](www.digitaldomain.com)
        else
                echo "Digital Domain"
        fi

elif [ $ans == "Industrial Light and Magic" ]; then
                firefox [www.ilm.com](www.ilm.com)
        else
                echo "Industrial Light and Magic"
        fi

---

### Post by BoyOfDestiny on 2009-03-02
Glad to help, You'd be better served by using a case statement, rather than if.

```
ans=$(zenity --list --text "Which site would you like to launch?" --radiolist --column "Pick" --column "Site" TRUE "Digital Domain" FALSE "Industrial Light and Magic");

case $ans in
 "Digital Domain")
 firefox www.digitaldomain.com
;;

 "Industrial Light and Magic")
 firefox www.ilm.com
;;
esac
```

---

### Post by penguinpazazzer on 2009-03-02
> **BoyOfDestiny said:**
> Glad to help, You'd be better served by using a case statement, rather than if.

```
ans=$(zenity --list --text "Which site would you like to launch?" --radiolist --column "Pick" --column "Site" TRUE "Digital Domain" FALSE "Industrial Light and Magic");

case $ans in
 "Digital Domain")
 firefox www.digitaldomain.com
;;

 "Industrial Light and Magic")
 firefox www.ilm.com
;;
esac
```

You have been tremendously helpful, THANK YOU!!!

---

### Post by penguinpazazzer on 2009-03-04
Since you were all super-helpful, I wonder if you could help me with this other issue... I also have to do a Maya MEL Scripting project and video presentation, but all of the tutorials I have found are either too simple, or don't really have a whole lot to do with MEL. There are a few on Highend3D that work ok, but I am wondering if any of you can recommend something?

Thanks!

---

