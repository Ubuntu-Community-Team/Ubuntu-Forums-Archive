---
title: "Korean Input"
date: 2012-10-31
forum: New to Ubuntu
---

### Post by yandy on 2012-10-31
When I was installing Ubuntu, I selected the Korean keyboard option as I live in Korea and would like to be able to input text in both English and Korean. However, now Ubuntu is up and running, it seems I cannot use Korean. Whenever I press the language key, a box drops down asking me to "*type your command*". Please help me.

Thanks

---

### Post by newb85 on 2012-10-31
The keyboard option you select needs to reflect the layout of the physical keyboard you're using.  "Type your command" is the Heads-up display, which would normally come up when the user hits the Alt key.  From the Dash, pull up Keyboard Layout.  In the bottom-left corner there should be a row of buttons, and the far-right one should look like a keyboard.  Click it, and check that the keyboard image that comes up looks like the physical layout of your keyboard.  

It's possible using an Input Method Editor to enter Korean with a non-Korean keyboard.  If that's what you need, we can go into more detail there.

---

### Post by yandy on 2012-11-01
Thanks for your quick reply. My keyboard is a Korean keyboard, so it has both Korean and English characters. When I installed Ubuntu I selected Korean layout. However, when I check the layout, as you explained, it shows a standard English keyboard, despite it being called "Korean". 

The "Alt" button to the right of the space bar should allow me to switch between languages, but for some reason this doesn't happen.  When I click on the keyboard icon at the top of the screen, it does give me the option to use Chinese input, which isn't of any use to me.

---

### Post by newb85 on 2012-11-01
First, open Language Support (from the Dash) and make sure Korean is in the list of languages.  (It's okay if it's greyed-out.)  If it's not, hit "Install/Remove Languages" and add it.  Also, make sure "Keyboard input method system" is set to ibus.

Then pull up Keyboard Input Methods (again, from the Dash) and go to the "Input Method" tab.  Make sure "Customize active input methods" is checked.  If a Korean IME isn't listed in the Input Method box, select it in the dropdown that says "Select an input method" and hit "Add".  (I believe the IME will have Hangul in the name.)

---

