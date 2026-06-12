---
title: "how can i make a program vs code by microsoft not to access the internet or limit it?"
date: 2019-10-26
forum: New to Ubuntu
---

### Post by ronjjjg8885 on 2019-10-26
thanks

---

### Post by uRock on 2019-10-26
Can you give more information as to what you're talking about? Are you using ubuntu as a firewall? Is the Windows app running in Wine or a VM?

The more information you give in your questions, the better people will be able to help.

---

### Post by SeijiSensei on 2019-10-26
Run it in a [virtual]("https://virtualbox.org/") Windows machine with no network adapter enabled.

---

### Post by Holger_Gehrke on 2019-10-26
[Visual Studio Code]("https://code.visualstudio.com/docs/setup/linux") may be developed by MS, but it actually runs on Linux and is available in either .snap or .deb packages. So the question comes down to : how can I stop a program from accessing the net ? This is complicated in this case by the fact that there are legitimate uses of net-connections for this program (it's an editor / IDE, specialised in web-app development and includes deployment tools for Microsoft Azure; it also integrates git and if I read it right can do remote debugging). So just denying it all net use in an apparmor profile is probably not the right idea.

On the other hand this raises the question why anyone would want to run a program he doesn't trust ...

Holger

---

### Post by zimbuf on 2019-10-26
Assuming there's no fallback logic for this, you could change its desktop launcher to instead launch a shell script.

At the top of this shell script, you could put some bogus HTTP_PROXY and HTTPS_PROXY variables to fool VS Code into thinking there are system proxy settings.

```

export HTTP_PROXY="http://foo.quux:8080/"
export HTTPS_PROXY="https://bar.quux:8080/"

code

```

Granted, this has the drawback of not being able to access the internet *at all* through the built-in terminal, if this solution works.

But in all honesty, you're better off building VS Code from source if you don't want to be tracked.

---

### Post by ubname on 2019-10-27
> **ronjjjg8885 said:**
> thanks

You can try VSCodium, VSC without telemetry:

[https://vscodium.com/](https://vscodium.com/)

---

