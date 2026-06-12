---
title: "Highlight active directory in terminal"
date: 2013-09-21
forum: New to Ubuntu
---

### Post by UlTroX2000 on 2013-09-21
Hello Ubuntu-Community,

I imagined my question to be quite common but I couldn't find anything about it using google or the forum search.
So here's my question:
At the computers in my university, the standard Ubuntu terminal highlights the active directory in green (I mean the "username@pcname:~/directorys$"-part when I enter a new command). I'd like to get the same highlighting on my laptop at home because I find it difficult to find the beginning of the error messages sometimes when programming (maybe the fact that I have so many error messages I have to scroll up in the terminal should tell me I'm not made for this, but sometimes those messages just get out of hand if you miss a singel ; in C++...). I checked the profile settings but couldn't find anything concerning this problem.

Can anybody tell me how to enable that functionality?

Thanks a lot in advance!
Jonathan

PS: I am using standard Ubuntu 13.04 on a Thinkpad T420s, if that is of any concern. The terminal is the standard terminal.

---

### Post by oldos2er on 2013-09-21
See [https://help.ubuntu.com/community/CustomizingBashPrompt#Setting_Prompt_With_Color](https://help.ubuntu.com/community/CustomizingBashPrompt#Setting_Prompt_With_Color)

---

### Post by whitesmith on 2013-09-21
If samples are your cup of tea, try: [http://www.cyberciti.biz/tips/howto-linux-unix-bash-shell-setup-prompt.html](http://www.cyberciti.biz/tips/howto-linux-unix-bash-shell-setup-prompt.html) (color examples in URL near bottom of page).

---

### Post by nerdtron on 2013-09-21
I remember it was set in the profile settings. But there are many colors there. I basically went on trial and error.
[http://www.youtube.com/watch?v=-JQHbAfwnKw](http://www.youtube.com/watch?v=-JQHbAfwnKw)

---

### Post by UlTroX2000 on 2013-09-22
Thanks a lot guys, this link did it: [https://help.ubuntu.com/community/CustomizingBashPrompt#Setting_Prompt_With_Color](https://help.ubuntu.com/community/CustomizingBashPrompt#Setting_Prompt_With_Color)

So basically, if you are happy with a green prompt line, you just have to do the following:
- Backup and open the .bashrc file in your home folder
- Search for the following line: **#force_color_prompt=yes**[COLOR=#333333][FONT=Ubuntu] 
- Remove the leading # sign and save the file.
[/FONT][/COLOR]

---

### Post by oldos2er on 2013-09-22
The last step would be ```
source .bashrc
```

---

### Post by vasa1 on 2013-09-22
> **oldos2er said:**
> The last step would be ```
source .bashrc
```
Is that only if a terminal was open while .bashrc was being edited?

---

### Post by UlTroX2000 on 2013-09-23
> **oldos2er said:**
> The last step would be ```
source .bashrc
```

I'm sorry but I can't follow you here. What does the source command do with the file? I did not do this and it worked, did I miss something?

EDIT: Seems like I found the solution myself. Apparently this reloads the settings for the currently running terminal. So closing the terminal and opening a new one should do the same, right?

---

### Post by mörgæs on 2013-09-23
Thanks for an attempt to marking the thread 'solved', but the best way is through Thread Tools. I have changed it now.

---

### Post by oldos2er on 2013-09-23
> **UlTroX2000 said:**
> Apparently this reloads the settings for the currently running terminal. So closing the terminal and opening a new one should do the same, right?

Right.

---

