---
title: "KDevelop Woes"
date: 2007-06-20
forum: Programming Talk
---

### Post by jlacroix on 2007-06-20
Hello everyone! I'm still rather new to programming. I'm studying Ruby as of right now, and I also study C++ and C#.

KDevelop seems like a nifty program so I installed it, and I can't get barely anything to run right. These are the problems I'm having with KDevelop right now, hopefully some of them can be resolved.

1.) When I am programming with Ruby, and I write a typical learning program, kind of like this:
```

puts 'Please enter something'
varTest = gets.chomp
puts 'You typed ' + varTest + '.'

``` 
The execution fails because the bottom window cannot accept input. If I go to the "Konsole" tab and manually type "ruby testprogram.rb" it will run fine. Is there a way to automatically make it pull up Konsole for this type of program?

2.) As far as C++ and C# go, if I load any of the QT or KDE application templates, they will not run AT ALL. Missing dependencies. I've been dependency hopping for a long time now and I can't get it resolved. Basically, what do I need to compile QT and KDE Cx programs?

Thanks in advance. I'm trying my best to learn programming and get good at it. Hopefully I can figure out the interface of KDevelop so I can actually put it to use.

---

### Post by jimmygoon on 2007-06-20
> **jlacroix said:**
> Hello everyone! I'm still rather new to programming. I'm studying Ruby as of right now, and I also study C++ and C#.

KDevelop seems like a nifty program so I installed it, and I can't get barely anything to run right. These are the problems I'm having with KDevelop right now, hopefully some of them can be resolved.

1.) When I am programming with Ruby, and I write a typical learning program, kind of like this:
```

puts 'Please enter something'
varTest = gets.chomp
puts 'You typed ' + varTest + '.'

```The execution fails because the bottom window cannot accept input. If I go to the "Konsole" tab and manually type "ruby testprogram.rb" it will run fine. Is there a way to automatically make it pull up Konsole for this type of program?

2.) As far as C++ and C# go, if I load any of the QT or KDE application templates, they will not run AT ALL. Missing dependencies. I've been dependency hopping for a long time now and I can't get it resolved. Basically, what do I need to compile QT and KDE Cx programs?

Thanks in advance. I'm trying my best to learn programming and get good at it. Hopefully I can figure out the interface of KDevelop so I can actually put it to use.

Don't know about the rest, but you need to search for qt DEV libraries... but a more specific error message would help debugging.

---

### Post by kknd on 2007-06-21
This should work:

sudo aptitude install kde-devel build-essential

---

### Post by jlacroix on 2007-06-24
Thanks!

---

