---
title: "[SOLVED] Some Python help please.."
date: 2008-11-06
forum: New to Ubuntu
---

### Post by MrJoeyUK on 2008-11-06
Hello all.. after a lengthy absence from Python I decided to give it another shot at learning it.

I'm playing around with raw_input and variables.. so I decided to make a simple conversion program... with dog years.. :), the code is as follows..

[B]print "Find out how old you are in dog years.."
str = raw_input("How old are you: ")
print "Age * 7 ="
str*7
[/B]
However when I run the program in IDLE the last calculation doesn't provide any output. The only output I recieve is as follows..

[B]Find out how old you are in dog years..
How old are you: 8
Age * 7 =[/B]

 Although if I do the input alone in the IDLE screen the calculation works perfectly. Am I doing something wrong here? To test it further I closed everything, reopened IDLE, CTRL+N, then did a simple 2+2.. ran it and it doesnt work, yet once again it does if ran straight in the IDLE prompt. 

There is probably a simple solution to this but for the life of me I can't figure it out. Any help in helping me to understand this would be greatly appreciated, thanks.

PS: sorry if this isn't really the right section to post this in..

---

### Post by g3k0 on 2008-11-06
try beginning the last line with print.  You may also need to cast the result to an integer int(str)*7

---

### Post by MrJoeyUK on 2008-11-06
Thank you g3k0.. it did indeed need print, and after that also needed the integer as it did some kind of weird calculation. Thanks!

---

