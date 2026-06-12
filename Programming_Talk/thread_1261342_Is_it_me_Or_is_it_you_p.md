---
title: "Is it me? Or is it you :p"
date: 2009-09-08
forum: Programming Talk
---

### Post by StrangersInTheDark on 2009-09-08
Hey guys whats up... I'm a big fan of linux. I develop between windows and linux (sometimes I have to test out different commercial browsers)

The problem I encounter from time to time is that. When I use Firefox in windows, chrome, safari etc etc. My layout looks fine from my css files.


But when I hop onto linux to check out the layout on Firefox some of the things are out of alignment.

For example: I may have two horizontal text boxes for a username/password entry.

On the windows machine the textbox lay on top of each other evenly.

When I go onto linux the same two boxes are on top of each other but the edges aren't even

windows 
    username:   -----------
                  password:   ----------- 

But when im testing under Linux the username and password textboxes aren't aligned like the above example. the password box for example would be indented to the right making it uneven to the top box

Is this just by nature how Linux OS handles CSS Files? I have read people sometimes detect which OS is being used and then switch CSS files for that particular Operating System. Any feedback will be good

-StrangersIntheDark

---

### Post by Reiger on 2009-09-08
I would suggest you do some background reading on CSS first. Whatever OS lies under the hood has nothing to do with how CSS files are (not) handled; and the assumption strikes me as in need of a background explanation. There's plenty of stuff about what CSS is and what it does; and I can't be bothered to type all of that right now. Not when I am debugging my own stuff. :P 

Now, I am therefore in doubt whether or not I should right now provide you with the most likely culprit (and if it is that, it is all "your own fault" :P) because you might rush to fix your issue with that and be none the wiser about CSS in general (and especially if it fixes your probem then you will probably run into more funky stuff in the future which will again provoke questions that are solved by some background reading)... but it can be summarized in one word: reset.css.

---

### Post by StrangersInTheDark on 2009-09-08
> **Reiger said:**
> I would suggest you do some background reading on CSS first. Whatever OS lies under the hood has nothing to do with how CSS files are (not) handled; and the assumption strikes me as in need of a background explanation. There's plenty of stuff about what CSS is and what it does; and I can't be bothered to type all of that right now. Not when I am debugging my own stuff. :P 

Now, I am therefore in doubt whether or not I should right now provide you with the most likely culprit (and if it is that, it is all "your own fault" :P) because you might rush to fix your issue with that and be none the wiser about CSS in general (and especially if it fixes your probem then you will probably run into more funky stuff in the future which will again provoke questions that are solved by some background reading)... but it can be summarized in one word: reset.css.

yeah you are probably not that far from the truth on that one. Its a big application and i'm mostly a back-end type of guy. But the application was scrap together pretty fast the Aesthetics side of it to allow more focus on what runs the application.

But yeah I think the best thing to do is come back to it and recode some of the css. It runs find on all browsers under windows including firefox. So I will continue to focus on that more considering 5% visitors will likey be using Linux.

But I will take care of the Linux after a few more tasks.

Thanks for tips. I just wanted a second opinion sense I was reading how other people switch out CSS after the script detects windows OS or Linux.

Cheers!

---

### Post by StrangersInTheDark on 2009-09-08
welll sh*t give me some credit..its not like its all rocket science. haha

But thanks for leaving feedback.

---

### Post by Can+~ on 2009-09-08
Most things about web programming are totally independant of the OS, forms are an exception.

Forms use the layout of the graphic enviroment, that's why you can see GTK+ styled buttons sometimes, for example:

[http://www.google.com/firefox](http://www.google.com/firefox)

the "Google Search" button is themed. Probably, the theming made things fit different and pushed some content making it adjust another way.

Now, to solve the issue, you can override this by making your own style buttons, [here's an example]("http://cssbutton.com/forms/"). Or by making extra room and forcing everything to fit (maybe width:auto and float:somewhere).

"Strangers in the night... exchanging glances. Wondering in the night..."

---

