---
title: "What does in your path mean?"
date: 2014-03-22
forum: New to Ubuntu
---

### Post by robertzito on 2014-03-22
I am trying to run an app on my Ubuntu 13.10 that is giving me an error "You need to have Ruby installed and in your PATH". I installed Ruby but I do not know what "in your path" mean or how to setit!

---

### Post by Vaphell on 2014-03-22
```
echo $PATH
```

$PATH lists 'approved' directories that will be searched if you run a command without explicit path.
When you run **ls** you don't have to type **/bin/ls**, because **/bin** is mentioned in $PATH.

you can create a symlink that will be stored in one of these approved locations or add the dir to PATH in ~/.profile

where did you install ruby? Another question: why didn't you use the one from repos, which should be configured properly out of the box?

---

### Post by TheFu on 2014-03-22
A "PATH" works the same on Linux as it does on every other OS.
Open a terminal and run **env|grep PATH**.  This will show a few different PATH-based environment variables that work in about the same way for different kinds of files on the system. The plain "PATH" is where executable programs are automatically searched when a program is not fully specified.

ls - for example.
without a PATH set, we'd have to type /bin/ls everytime to run that program.

Every userid can control their own path, but if you've used apt-get to install ruby, the program will be placed in your path automatically. If you are running bash as your shell - the default - nothing more is needed.  With other shells, you might need to run a built-in program to reread the PATH, that is usually **rehash**.

---

### Post by robertzito on 2014-03-22
[COLOR=#000000][Vaphell]("http://ubuntuforums.org/member.php?u=347382") [/COLOR]I used this method for installation [http://gorails.com/setup/ubuntu/13.10](http://gorails.com/setup/ubuntu/13.10) and in usr/bin I see a symbolic link ruby and there is ruby 2.0 and 1.9.1 that lets me select what I want the default to be. Here is the output of path /usr/local/heroku/bin:/home/me/bin:
/usr/lib/lightdm/lightdm:
/usr/local/sbin:
/usr/local/bin:
/usr/sbin:
/usr/bin:
/sbin:
/bin:
/usr/games:/usr/local/games

And btw [[COLOR=#000000]Korkel[/COLOR]]("http://ubuntuforums.org/member.php?u=1911151")[COLOR=#000000] , that is why I posted this in absolute beginner and not I am a pro and know everything there is to know about ubuntu! [/COLOR]

---

### Post by TheFu on 2014-03-22
A $PATH shouldn't have spaces, newlines, CRs.  It needs to be one, unbroken, line with ':' characters separating directories.

Loading Ruby to learn ruby development is a complex thing for the uninitiated.  My ruby group has weekly - how-to-install sessions to help noobs.  I'm happy to see you trying to follow a best practice by using rbenv or rvm - that is smart, but it puts extra skill and extra knowledge on YOU to understand how the computer works.  We've all been there.  At the beginning RoR class, we spend 2 sessions helping people setup their RoR development environment.

Try to find local help to get this working. That is my only good suggestion.

In the meantime, if you just want to run a RoR app - use the Ubuntu repo version of Ruby and Rails.

---

