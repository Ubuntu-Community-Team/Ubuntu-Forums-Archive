---
title: "Ubuntu Selection Issues"
date: 2012-06-20
forum: New to Ubuntu
---

### Post by Viraldemon on 2012-06-20
Ok, this is probably going to sound ridiculous, but the selection on ubuntu is driving me nuts!

On windows, say I wanted to select the world "HELLO". I could start my cursor in the middle of the "H" and drag right. On linux I have to start my cursor in the middle of the letter or space before the "H". But since I'm used to selecting from the middle of the letter I want to select, I end up selecting "ELLO" instead of "HELLO".

This is a huge pain because I am constantly copy and pasting. I realize that if I did it long enough I would eventually get used to selecting properly, but now I constantly go between linux and windows, and this is going to drive me insane.

Is there a secret setting somewhere that I can adjust to get more windows-like behavior? I'm not complaining because I think the windows way is better, I'm just used to it.

Also I'm using the latest version of the Ubuntu Desktop available, running on vmplayer.

Edit2: Ok, the exact thing that gets me is this: In windows if you select [to the right] from the exact center of a letter, it selects that letter. In linux, it skips that letter. This seems to be system-wide. (Except for the terminal. Compare and contrast selection between the terminal and a textbox if you want to see what I mean)

---

### Post by cortman on 2012-06-20
> **Viraldemon said:**
> Ok, this is probably going to sound ridiculous, but the selection on ubuntu is driving me nuts!

On windows, say I wanted to select the world "HELLO". I could start my cursor in the middle of the "H" and drag right. On linux I have to start my cursor in the middle of the letter or space before the "H". But since I'm used to selecting from the middle of the letter I want to select, I end up selecting "ELLO" instead of "HELLO".

This is a huge pain because I am constantly copy and pasting. I realize that if I did it long enough I would eventually get used to selecting properly, but now I constantly go between linux and windows, and this is going to drive me insane.

Is there a secret setting somewhere that I can adjust to get more windows-like behavior? I'm not complaining because I think the windows way is better, I'm just used to it.

Also I'm using the latest version of the Ubuntu Desktop available, running on vmplayer.

Edit2: Ok, the exact thing that gets me is this: In windows if you select [to the right] from the exact center of a letter, it selects that letter. In linux, it skips that letter. This seems to be system-wide. (Except for the terminal. Compare and contrast selection between the terminal and a textbox if you want to see what I mean)

I'm able to click the middle of a letter and select it. But frankly, with any font smaller than enormous this is splitting hairs, almost literally. I don't see how you can be precise enough to grab the middle, left, or right side of a 12 point "i" or "t" to make a difference.
Sorry it's a bother, but I don't think there's much to do about it (results of a google search)- there's an old [Gedit plugin]("http://ubuntuforums.org/showthread.php?t=1360169") available for something similar, but that's as close as I could find.

---

### Post by Viraldemon on 2012-06-20
Actually I'm afraid the issue addressed in that link is very unrelated and specific to gedit unfortunately. (But thank you for trying to help)

I am talking about something that is system wide, except in the terminal.

And it is very easy to select left, middle, right part of each individual letter. The thing is it's usually unconscious. If you've used linux a ton, you probably automatically move all the way to the left when you want to select something.

Again, to see the difference select something in the terminal, vs in any textbox. Use a nice big letter like H in the world Hello
If you select from the middle, or even the right side of the letter H it selects the entire letter in the terminal (and in windows). However in the rest of linux selecting the middle or right side of a letter will ignore that letter and select the next letter. Also, this is only visible when you select from left to right.

I am guessing that the constant that decides what letter you've selected is probably hard coded somewhere deep in linux's text-renderer or something like that. But if someone knows where/how to change it, that would save me from having to re-learn how to select things every time I change computers.

---

### Post by coffeecat on 2012-06-20
If I want to select a single word, I simply position the cursor anywhere over the word and double-click. Triple-clicking seems to vary according to application and highlights to the end of the line, the current sentence or the current paragraph.

---

### Post by Viraldemon on 2012-06-20
No I'm afraid selecting an entire word is not what I'm doing either. I am a developer and I usually want to select very particular parts of expressions which are often not whole words, or involve many words or w/e.

I don't have a problem with the major changes from windows to linux, but this subtle difference is causing me ridiculous amounts of pain because I'm having to relearn to select text. Something I do very automatically unfortunately =S

---

### Post by blackbird34 on 2012-06-20
*If you want to select a whole word, you can just double click the word in question. For a paragraph, 3 or 4 clicks in quick succession. *
[B]Using Shift plus the arrow keys is also a nice precise way of selecting. If You add Ctrl to the mix, it selects whole words at a time. 

I discovered all this by accident as shift, ctrl and the arrow keys are right next to each other on my keyboard. I never click-drag with the mouse to select words now. Or hardly ever... [/B] 

Plus I think all this works on Windows/Mac too :D

Edit: oh bother, duplicate, useless post... forget the start.

---

### Post by Viraldemon on 2012-06-20
> **blackbird34 said:**
> *If you want to select a whole word, you can just double click the word in question. For a paragraph, 3 or 4 clicks in quick succession. *
[B]Using Shift plus the arrow keys is also a nice precise way of selecting. If You add Ctrl to the mix, it selects whole words at a time. 

I discovered all this by accident as shift, ctrl and the arrow keys are right next to each other on my keyboard. I never click-drag with the mouse to select words now. Or hardly ever... [/B] 

Plus I think all this works on Windows/Mac too :D

Edit: oh bother, duplicate, useless post... forget the start.

Thank you for trying to help. I am well aware of using shift and ctrl. I do use these in certain circumstances, however I tend to rely on the mouse when copying and pasting because then I don't have to move my hands. I can press ctrl+c/v with my left hand and operate the mouse with my right.

Moving my right hand to the keyboard to control the arrow keys is more effort honestly. I probably sound crazy, but over the years of developing on windows I've fallen into these sort of habits for maximum efficiency.

Is there really no way to change the behavior of the text selection? There's not just an editable offset in some text file somewhere? Does no one else notice this?!


**Problem resolved!** I'm not entirely sure what caused the issue I explained in the above posts, but it definitely has something to do with using Ubuntu through VMWare. After I installed it on an actual computer I no longer experienced this issue, and now I select things as I expected to all along.

---

