---
title: "Plymouth command failed"
date: 2013-10-13
forum: New to Ubuntu
---

### Post by Filip_Lundberg on 2013-10-13
Ubuntu doesn't  work for me so I need help asap. After have been online on the computer for some minutes this pops up
[http://tinypic.com/r/wbs4nd/5](http://tinypic.com/r/wbs4nd/5) "Plymouth command failed". And when that happened. I can't do anything on the computer :/

I don't know what's wrong.

I have read a lot of threads but none has worked for me :/

I hope someone can help me, thank you :)

---

### Post by andreazzz on 2013-10-14
Have you already tried ```
sudo dpkg --configure -a
```? Most times this will solve the problems. Other possibilities: sudo apt-get update -y && sudo apt-get upgrade -y
Else you should try locate broken packages with aptitude: sudo aptitude . It should be possible to use your mouse in the terminal, click on one of the most right menu-items and select "mark broken packages" or something like that. If there are any, you will see them together with options to fix them.

---

### Post by Filip_Lundberg on 2013-10-17
Maybe this is the problem? [http://tinypic.com/r/2isidm9/5](http://tinypic.com/r/2isidm9/5)

and this [http://tinypic.com/r/33bekqg/5?](http://tinypic.com/r/33bekqg/5?) How do I fix this U think?

---

### Post by andreazzz on 2013-10-17
To be really honest, my Norwegian/Finnish/Danish/Swedish* is not that great, so could you translate the errors for me?(:

Are you able to update through terminal using [sudo apt-get update] and the other commands I gave in post #2? [sudo dpkg --reconfigure -a] might solve the problems. After all that, try [sudo apt-get autoremove] and [sudo aptitude].

*I am not responsible for any harm caused by an incorrect interpretation of this assumption.

---

### Post by Filip_Lundberg on 2013-10-20
Message 1: An unresolvable problem occurred while calculating the upgrade .

Please report this bug against the 'update manager' package and include the following error message 
'E:error, pkgProblemResolver::Resolve generated break; This can be caused on withheld packages.
It usually means that your installed packages has Dependencies who's not satisfied.

[B]
Do you know What I Should do to fix this or Should I report this?
[I]
If you don't know how I Should do to fix this I have another question for you:

[/I]
[/B]Should I report the bug like the picture( who was on Swedish) Or should I translate for them?

---

### Post by andreazzz on 2013-10-20
Well, it seems there are problems with some packages. Have you tried fixing them with the commands I supplied you with? And with aptitude?
If yes: my knowledge ends here. If not: try them, it might work.

I don't really know. You might translate it, but I do not think it is necessary for them.

P.S. you can make screenshots with [alt]+[printscreen]

---

### Post by Filip_Lundberg on 2013-10-24
None of your commands world :( But How do I report this bug and What is the thing that I Should report?

---

### Post by sandyd on 2013-10-24
Its a bug with the WL driver (broadcom)
[https://bugzilla.redhat.com/show_bug.cgi?id=896587](https://bugzilla.redhat.com/show_bug.cgi?id=896587)
[https://bbs.archlinux.org/viewtopic.php?pid=1223933](https://bbs.archlinux.org/viewtopic.php?pid=1223933)
[https://retrace.fedoraproject.org/faf/problems/327785/](https://retrace.fedoraproject.org/faf/problems/327785/)

---

### Post by Filip_Lundberg on 2013-10-31
The problem was the STA driver, I have now changed to the b43 instead ;)

---

