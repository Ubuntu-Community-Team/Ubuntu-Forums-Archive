---
title: "python tk interactive widget"
date: 2010-03-29
forum: Programming Talk
---

### Post by radon7 on 2010-03-29
I am trying to find a widget that will work as an interactive widget as a console.  I want to create a tk widget and run os.system('bash') or os.system('cmd.exe') in a widget to have a terminal.

I know there are a lot of terminal programs out there but I haven't found one using tk and I'm trying to incorporate a terminal into another program that will work using python only so that it will work on about any system.

Everything I have read has pointed to the Text or Canvas widgets but I haven't been able to get os.system('bash') to run in it.

Thanks in advance.

---

### Post by wmcbrine on 2010-03-29
Well, you don't want os.system() for this, because you need to redirect the input and output to your widget. Look into the subprocess module.

---

### Post by radon7 on 2010-04-04
OK I'll check out subprocess but can anyone tell me how to redirect input and output to the widget and what widget I should use(text canvas or???)?

---

