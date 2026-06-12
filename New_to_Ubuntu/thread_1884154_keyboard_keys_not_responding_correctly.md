---
title: "keyboard keys not responding correctly"
date: 2011-11-20
forum: New to Ubuntu
---

### Post by mrvn on 2011-11-20
Hi I'm still fairly new to using Ubuntu. Right now I am currently running 11.04. Recently my keys on my keyboard stopped responding correctly. When I enter in the "0" key the output is /, when I enter "j" I get the number 1, when I type" k" I get 2 and "l" is 3, when  I enter";" the output is  -  and" n" is 0 and the"?" gives me a + . This is highly annoying and I have no clue what to do to fix my problem can anyone please help me ?

---

### Post by oldsoundguy on 2011-11-20
> **mrvn said:**
> Hi I'm still fairly new to using Ubuntu. Right now I am currently running 11.04. Recently my keys on my keyboard stopped responding correctly. When I enter in the "0" key the output is /, when I enter "j" I get the number 1, when I type" k" I get 2 and "l" is 3, when  I enter";" the output is  -  and" n" is 0 and the"?" gives me a + . This is highly annoying and I have no clue what to do to fix my problem can anyone please help me ?

Try another keyboard.  If you do not have one, pick up a spare at some thrift store. Should cost about $5 US.

---

### Post by jjex22 on 2011-11-20
Also check you haven't changed your keyboard or locale settings - don't worry you don't need to use the keyboard just browse from the launcher

---

### Post by mrvn on 2011-11-20
> **oldsoundguy said:**
> Try another keyboard. If you do not have one, pick up a spare at some thrift store. Should cost about $5 US.

buying a new keyboard is not an option, I should have mentioned I'm working with a laptop. I know the keyboard still works. I booted up my laptop with other distros and the keys worked out  only when I boot up ubuntu things start acting strange. I checked to make sure I have the right layout under keyboard preferences and everthing is correct. I know this is a problem with my settings what other options should I check out ?

---

### Post by jjex22 on 2011-11-20
If you can work out enough of the keys you can try running loadkeys - for uk/us try:

loadkeys us
loadkeys uk (if it doesn't find it try gb)

but you have to do this outside the gui - either ctrl-alt-F1, or restart in CLI mode - you'll have to restart after. the only trouble is you have to work out where the characters are now located on your keymap -including your password and username to sign in.

---

### Post by mrvn on 2011-11-20
even more of my keys stop working when I swith to log in. when I enter "loadkeys us" from the terminal I get a message "Couldn't get a file descriptor referring to the console"

---

### Post by Kelvari on 2011-11-20
It sounds to me like your NumLock has been turned on. The keys that you mention double as the laptop's number pad.

Do you have a key that has what looks like 3 or 4 rows of boxes on it? You may have to hold the Function button (generally labeled Fn or something to that effect) while you press it to turn it off.

---

### Post by mrvn on 2011-11-20
you are correct i just have to figure out how to turn it off

---

### Post by mrvn on 2011-11-20
[Kelvari]("http://ubuntuforums.org/member.php?u=409999") thanks!  that was a super easy problem to solve.

---

### Post by Kelvari on 2011-11-20
Glad I was able to help :D Sadly, sometimes the easiest, simplest solutions are the most effective ones.

---

