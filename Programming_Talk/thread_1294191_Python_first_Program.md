---
title: "Python first Program"
date: 2009-10-18
forum: Programming Talk
---

### Post by Sliiice on 2009-10-18
So i have gone through 2 tutorials and I am diving into a simple program. I want to make a simple search return style program. My goal is to create a simple python program where you can enter in the Elemental symbol and receive a molar mass value. I have read about dictionaries however I am not quite sure as to where to start. I figured I should create a variable that is a str that is entered by the user Then use that str to compare to a dictionary and return a value. Any help would be appreciated 


                                                                                           -Sliiice

---

### Post by nvteighen on 2009-10-18
> **Sliiice said:**
> So i have gone through 2 tutorials and I am diving into a simple program. I want to make a simple search return style program. My goal is to create a simple python program where you can enter in the Elemental symbol and receive a molar mass value. I have read about dictionaries however I am not quite sure as to where to start. I figured I should create a variable that is a str that is entered by the user Then use that str to compare to a dictionary and return a value. Any help would be appreciated

-Sliiice

Well, your idea seems pretty good. Some ideas that might help you:

1) Separate the processes of "setting the dictionary up", "searching in the dictionary", "getting input from user" and "showing output to the user". Use functions for that; you'll have to think a bit how to connect them in order to get it right (i.e. interface design... functions' parameters and return values), but I believe it's easy if you think a while on how to do it and test some alternatives.

2) Dictionaries accept any immutable objects as "keys". Take that in account and you'll be able to bypass any input processing in order to get the value.

3) Dictionaries accept anything as "values" for keys... With a little imagination (and if you want), you could quickly make your dictionary very extensible for further atomic properties. Of course, that will need to create some custom accessors in order to get the queried information.

Please post any of your advances! And good luck! :D

---

