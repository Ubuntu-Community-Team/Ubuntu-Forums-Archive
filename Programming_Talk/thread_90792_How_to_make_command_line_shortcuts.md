---
title: "How to make command line shortcuts"
date: 2005-11-15
forum: Programming Talk
---

### Post by rosslaird on 2005-11-15
I ssh into a remote server several times each day. I dutifully type in:

ssh myusername@remotehostname:/dir/I'm/looking/for. 

This takes forever. Is there a way to shortcut the typing (I already have password-less login configured, so at least that is quicker). Even just a shortcut for the username and hostname would be good. I do use the up arrow to find the previous entry, but often I've done dozens of other commands since I logged into the server, so sometimes the up arrow repeating takes longer than the typing...

I'd like to be able to type: ssh web

Thanks.

Ross

---

### Post by DJ_Max on 2005-11-15
You could add a line such as
```

export WEB=myusername@remotehostname:/dir/I'm/looking/for

```
In your ~/.bashrc file. (If you edit this in a console window, you must open a new one for changes to take effect.)

Then you can do
```

ssh $WEB

```

---

### Post by Retrix on 2005-11-15
Bash has a number of ways to reduce typing...

First of all is aliases. Add something like the following to your ~/.bashrc file:
  alias sshtox='ssh user@remote:/dir/to/be/in'
Logout and back in (or type 'source ~/.bashrc' at a shell) and you can now perform the command by just typing 'sshtox'.

Another handy trick is to use Ctrl+r. This does a search through your recently typed commands. Hit Ctrl+r and start typing a part of the command you remember typing and bash will find it for you. Hit Ctrl+r again to scroll through the choices.

Alternatively, DJ_Max's suggestion is just as valid.

---

### Post by toojays on 2005-11-15
In general, Retrix's suggestion of using a bash alias is a good one. For the specific case of typing "ssh web" to get to your webserver, check out the documentation for ssh_config. You can modify your ssh config file so that it applies specific options when you ask to ssh to "web".

---

### Post by rosslaird on 2005-11-16
Thanks very much for all the tips and suggestions. This is going to make things much easier.

Ross

---

