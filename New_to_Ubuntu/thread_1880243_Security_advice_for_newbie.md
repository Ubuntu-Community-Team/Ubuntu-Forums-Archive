---
title: "Security advice for newbie"
date: 2011-11-13
forum: New to Ubuntu
---

### Post by bedpotato on 2011-11-13
Hello. I installed Ubuntu yesterday and am going to be using my browser for online banking and comping so security is important to me. I have already installed Firefox add-ons such as HTTPS Everywhere and No Script but am not sure if that will be enough.

I know the firewall question comes up a million times but can someone please help me? Are there any other things I will need to do, (such as which ports to open or close, how to go about doing so, and  any recommended firewall programmes), or am I fine to go ahead and use the Internet with the way things are now? I am a very paranoid person which is the main reason I am switching to Linux. I don't know how to type in computer language so if anyone can tell me things I should type into a terminal to make changes to any ports I would be grateful. I have been reading through this thread:

[http://ubuntuforums.org/showthread.php?t=1873643&highlight=security+newbie](http://ubuntuforums.org/showthread.php?t=1873643&highlight=security+newbie)

but so far there does not seem to be a FAQ or tuturial on how to set up basic security for clueless people.

---

### Post by Paddy Landau on 2011-11-13
Linux comes with basic security built in. This is a recurring question from people who come from Windows (yes, I was one of those once).

If you are not behind a router, you can turn on your firewall, but if you are behind a router with its own firewall, you're OK.

EDIT: see [post=11298747]one of my posts[/post] for turning on the firewall.

---

### Post by 2F4U on 2011-11-13
It is relatively easy to setup a firewall in Ubuntu. Open a terminal and type

sudo ufw status

This reports whether the firewall is enabled or not. To enable it, just type

sudo ufw enable

The most simple rule is to disable any incoming connection. You can do this by typing

sudo ufw default deny

---

### Post by bedpotato on 2011-11-13
Thank you very much! Yes, I have a wireless reuter. Will it have a firewall built-in?

---

### Post by Paddy Landau on 2011-11-13
> **bedpotato said:**
> Will it have a firewall built-in?
Check your router's manual. But, if it's a modern one, it almost certainly will.

---

### Post by fractalman on 2011-11-13
There's no need to worry that much, linux is far more secure than windows, and the majority of users have been in your shoes, coming to linux still with a windows mindset is a common occurence so don't stress too much,  install gufw,  the gui for your firewall if you don't want to use a terminal, but you should be pretty secure with what you have already  also get   chkrootkit rkhunter  to scan for rootkits, but to be honest if you're just an average joe doing normal everyday stuff on your pc then why would anyone waste time trying to hack you?

---

### Post by bedpotato on 2011-11-13
> **fractalman said:**
>  if you're just an average joe doing normal everyday stuff on your pc then why would anyone waste time trying to hack you?

It's not really hacking I'm worried about. As you rightly point out, I am not a celeb so I don't think anyone's going to be hacking into my computer to steal pictures of me. It's more Identity Theft and having my bank or Paypal details stolen that worries me.

---

### Post by Paddy Landau on 2011-11-13
The latest browsers come with (limited) warnings if you go onto sites that have been reported as scams.

Install the [WOT (Web of Trust)]("https://addons.mozilla.org/en-US/firefox/addon/wot-safe-browsing-tool/") add-on for some extra security, but of course remain vigilant when doing any banking.

---

### Post by Dangertux on 2011-11-13
> **bedpotato said:**
> Hello. I installed Ubuntu yesterday and am going to be using my browser for online banking and comping so security is important to me. I have already installed Firefox add-ons such as HTTPS Everywhere and No Script but am not sure if that will be enough.

I know the firewall question comes up a million times but can someone please help me? Are there any other things I will need to do, (such as which ports to open or close, how to go about doing so, and  any recommended firewall programmes), or am I fine to go ahead and use the Internet with the way things are now? I am a very paranoid person which is the main reason I am switching to Linux. I don't know how to type in computer language so if anyone can tell me things I should type into a terminal to make changes to any ports I would be grateful. I have been reading through this thread:

[http://ubuntuforums.org/showthread.php?t=1873643&highlight=security+newbie](http://ubuntuforums.org/showthread.php?t=1873643&highlight=security+newbie)

but so far there does not seem to be a FAQ or tuturial on how to set up basic security for clueless people. 

The Wiki being created in association with that thread is coming along okay, though it's still a work in progress. I suggest if there are things that you would like to see mentioned or discussed in it please feel free to ask about them in the thread while some of us are still working on the project.

The afforementioned wiki can be found here : [https://wiki.ubuntu.com/BasicSecurity](https://wiki.ubuntu.com/BasicSecurity)

As far as guides and tutorials go here are some pretty basic / general ones.

Creating a Firewall : [http://ubuntuforums.org/showthread.php?t=1876124](http://ubuntuforums.org/showthread.php?t=1876124)
Ubuntu General Security (this is pretty comprehensive) : [http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

Hope this is helpful.

---

