---
title: "Terminal password won't work"
date: 2008-07-15
forum: New to Ubuntu
---

### Post by AADude on 2008-07-15
My terminal:

> 
stephen@stephenpc:~$ su
Password:
su: Authentication failure


I type in:
> 
su [enter]
my password [enter]


And the password is correct, I logged in with it a few minutes ago... any help please? By the way I know it doesn't show the characters you type for password, and I press the right keys... so idk :/

---

### Post by sdennie on 2008-07-15
You don't need to use su for root access.  The reason it's not working is because "su" tries to login as root and the root password is disabled by default.  See: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by bobnutfield on 2008-07-15
Unless you have created a "root" account, this will not work.  Ubuntu uses "sudo" for admin duties instead of the "root" used by other distros.  If you need to do something requiring admin priviledges, just type sudo first, then the command.  You will be asked for your password, which is your normal user password.

---

### Post by Vivaldi Gloria on 2008-07-15
In a default ubuntu install the root password is a random hidden password. You can use your own password to use sudo & gksudo because the first user created has admin rights. But that pswd it your pswd, not root's. So you cannot su with that passwd.

---

### Post by YaroMan86 on 2008-07-15
If you want to switch to root for a time in the terminal, simply do this:

```

sudo su

```

However, I don't recommend being root. Using plain old sudo is a very secure and easy way to do things as root... without BEING root.

---

### Post by LowSky on 2008-07-15
you can always use "sudo -i" if yo dont want to type sudo countless times

---

### Post by Joeb454 on 2008-07-15
> **YaroMan86 said:**
> If you want to switch to root for a time in the terminal, simply do this:

```

sudo su

```

However, I don't recommend being root. Using plain old sudo is a very secure and easy way to do things as root... without BEING root.
Not the way I'd recommend doing things, though I can't be bothered to explain :D
> **LowSky said:**
> you can always use "sudo -i" if yo dont want to type sudo countless times

That's how I do it (especially on my server) I just use ```
sudo -i
```

---

### Post by Dr Small on 2008-07-15
> **YaroMan86 said:**
> If you want to switch to root for a time in the terminal, simply do this:

```

sudo su

```

However, I don't recommend being root. Using plain old sudo is a very secure and easy way to do things as root... without BEING root.
2 years ago, when I joined, everyone yelled:
```
sudo su
```

But now we are singing a new tune. Why?

---

### Post by coffeecat on 2008-07-15
**AADude**, previous posters have more or less said it all, but for the officlal version, have a look at this: [RootSudo]("https://help.ubuntu.com/community/RootSudo").

---

### Post by Vivaldi Gloria on 2008-07-15
> **Dr Small said:**
> 2 years ago, when I joined, everyone yelled:
```
sudo su
```

But now we are singing a new tune. Why?

I have been actively writing in this forums for about a month and I keep reading "It's against the forum policy to tell users how to become root blah blah" and such stuff. So I go along with it and keep "sudo su" etc to myself. When was that policy started?

---

### Post by Dr Small on 2008-07-15
> **Vivaldi Gloria said:**
> I have been actively writing in this forums for about a month and I keep reading "It's against the forum policy to tell users how to become root blah blah" and such stuff. So I go along with it and keep "sudo su" etc to myself. When was that policy started?
Well, things have really been heated since April, but I think alot of people misread the Forum Policy thread:
[http://ubuntuforums.org/showthread.php?t=765414](http://ubuntuforums.org/showthread.php?t=765414)

From the first line:
> Tutorials explaining how to _enable the root account for a graphical login_ or _autologin_ will not be supported on the forums and will be moved to the Jail.

People read the thread title and misinterpret the entire meaning of it. Because when I began Ubuntu, I was taught "sudo su". But now it seems to be a crime to say it...

---

### Post by AADude on 2008-07-15
Thanks everyone. I used sudo -i because I saw it first on that RootSudo page :).

---

### Post by Vivaldi Gloria on 2008-07-15
> **Dr Small said:**
> Well, things have really been heated since April, but I think alot of people misread the Forum Policy thread:
[http://ubuntuforums.org/showthread.php?t=765414](http://ubuntuforums.org/showthread.php?t=765414)

From the first line: ...

People read the thread title and misinterpret the entire meaning of it. Because when I began Ubuntu, I was taught "sudo su". But now it seems to be a crime to say it...

Hmm. So it's OK after all to become root temporarily in a terminal. Thanks mate.

---

### Post by coffeecat on 2008-07-15
> **Vivaldi Gloria said:**
> I have been actively writing in this forums for about a month and I keep reading "It's against the forum policy to tell users how to become root blah blah" and such stuff. So I go along with it and keep "sudo su" etc to myself.

'sudo su' is in that official Ubuntu documentation page that I linked. I believe the forum policy is about not revealing how to enable root login, which is quite a different matter

---

### Post by Vivaldi Gloria on 2008-07-15
> **coffeecat said:**
> 'sudo su' is in that official Ubuntu documentation page that I linked. I believe the forum policy is about not revealing how to enable root login, which is quite a different matter

Yep. Read it completely now. Appreciated. :)

---

### Post by coffeecat on 2008-07-15
> **Vivaldi Gloria said:**
> Yep. Read it completely now. Appreciated. :)

I posted to reply to your post which was last on the first page without seeing that there was a second page with about 4 posts. :oops:

---

### Post by Vivaldi Gloria on 2008-07-15
> **coffeecat said:**
> I posted to reply to your post which was last on the first page without seeing that there was a second page with about 4 posts. :oops:

Appreciated anyway. :-)

---

### Post by t0p on 2008-07-15
> **Vivaldi Gloria said:**
> I have been actively writing in this forums for about a month and I keep reading "It's against the forum policy to tell users how to become root blah blah" and such stuff. So I go along with it and keep "sudo su" etc to myself. When was that policy started?

Damn stupid "policy" if you ask me.  Condescending.  "Ooh, the newbies are too stupid to be trusted with root access." Grrr...

```
sudo su
```

```
sudo -s
```

```
sudo passwd root
```

Remember the saying: "Ubuntu is *yours* - if you break it, you get to keep both bits"?  Well, let the newcomers take chances with their OS.  All this wrapping-in-cotton-wool treatment doesn't do anyone any favours!

---

### Post by Dr Small on 2008-07-15
I think (now this is just my personal opinion) that having this policy in tack in really sheltering users, rather than making them more aware about risks, or even making them better Linux users and more knowledgable.

On ArchLinux, right after the install, there is only one user, and that is root. Security risk? None at all. Why? Because there is no services, nor anything installed on the system at this point. Networking hasn't even been setup.

The point is, I believe we are babying the users too much, which doesn't make them any more knowledgable.

Dr Small

---

