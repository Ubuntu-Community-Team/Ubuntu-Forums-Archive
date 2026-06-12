---
title: "false  display settings - how to reset them ?"
date: 2011-09-14
forum: New to Ubuntu
---

### Post by Eoe on 2011-09-14
hello ! ):P

I' m an absolute new user (and yet absolute friend of Ubutu ).

The point is this one : I installed correctly Ubuntu ( from my self-learn Windows background ) ;

While trying some settings, about speciaI effects and themas, I make an stupid error : put the size of fonts very too big ; since, I cannot get a correct display,- that  only concerning windows , - screen display by itself is OK.

and, as all the windows display is wrong I cannot reset it, 'cause when I click on a button, it doesn't do what I was waiting, directly, as it seems for the problem by itself ( I told tou I was still an autodidact-windows user   )   - I try to explain that clearly but it' s difficult :popcorn:.
- I do not actually know the vocabulary.

In system > screens , a box ask me ' wanna do use the owner's driver for your graphic card ( nvidia Gforce 400 ) or the X server" , or some things like that..

I do not understand ](*,) and again and again lost in all these windows, buttons ....

I' m rather stupid, I think ; so if a nice person can help me, I will be happy to enter the community :p:roll:

Thank you very much.

---

### Post by Krytarik on 2011-09-14
To reset all font settings to the defaults, do this:

1. At the login screen, press Ctrl+Alt+F1 to switch to the console.

2. Log in there.

3. Run these commands:
```
gconftool-2 --unset /desktop/gnome/interface/font_name
gconftool-2 --unset /desktop/gnome/interface/document_font_name
gconftool-2 --unset /desktop/gnome/interface/monospace_font_name
gconftool-2 --unset /apps/nautilus/preferences/desktop_font
gconftool-2 --unset /apps/metacity/general/titlebar_font
```4. Switch back to the login screen by pressing Ctrl+Alt+F7 or F8.

Greetings.

---

