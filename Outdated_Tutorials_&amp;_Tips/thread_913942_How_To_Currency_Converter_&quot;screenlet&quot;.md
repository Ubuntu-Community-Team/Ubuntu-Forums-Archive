---
title: "How To: Currency Converter &quot;screenlet&quot;"
date: 2008-09-08
forum: Outdated Tutorials &amp; Tips
---

### Post by nesh87 on 2008-09-08
Hello,

To begin with, i have searched and searched for a currency converter screenlet. I couldnt find anything similar to Vista's or OSX's currency converters. I was tired of googling the conversions, so i thought i'd use google's converter into a script.

Ive used PYGTK to create a small python application that takes the user's options, queries google using w3m, and returning the currency conversion rate.

Ive removed the window borders and controls to make it look more like a screenlet. To add it to the Widget-Layer:

1- Make sure you have Compiz
2- Go to System -> Preferences -> Advanced Desktop and Settings Affects
3- Enable the Widget Layer if you havent already
4- Navigate to the Behaviour Tab in the Widget Layer Options
5- Add this to the Text Entry: "title=Currency Converter" (w/0 the ")

Now put the script in whichever directory you like, and call it using :
[PHP]python direcotry/currency.py[/PHP]

So if you have it in your home folder:
[PHP]python ~/currency.py[/PHP]


If you decide you like the script and want to add it on startup, Open System->Preferences->Sessions and add the same command you used above.

Since this is only for personal use, ive added the currency i most commonly use. However, i made the currencies constants in the scripts, so all you have to do is open the script and change the constants CUR1, CUR2, CUR3 to the currencies you wish to have:

[PHP]
#Change the currencies as you wish.
CUR1 = "AUD" #Australian Dollar
CUR2 = "USD" #United-States Dollar
CUR3 = "KWD" #Kuwait Dinar


class Currency:
[/PHP]

[[IMG]http://b.imagehost.org/t/0833/currency.jpg[/IMG]](http://b.imagehost.org/view/0833/currency.png)

[[IMG]http://b.imagehost.org/t/0139/currency-screenlets.jpg[/IMG]](http://b.imagehost.org/view/0139/currency-screenlets.png)

Once again, if this has been done i didnt know and i have searched for one.

---

### Post by farahf on 2009-05-07
You can use the **Stocks** screenlet

I'm using it for British pound to US dollars

The key is to change the stock symbol

in this case it is GBPUSD=X


Here's How:


1-First start/launch the Stocks screenlet
2-right click it->properties->options->stocks
3-Change the stock symbol

---

### Post by lukeinvancouver on 2009-06-02
> **farahf said:**
> You can use the **Stocks** screenlet

I'm using it for British pound to US dollars

The key is to change the stock symbol

in this case it is GBPUSD=X


Here's How:


1-First start/launch the Stocks screenlet
2-right click it->properties->options->stocks
3-Change the stock symbol


Where do you find this stock screenlet? I searched and the system found nothing.


Added: OK that was a dumb question but the google list includes pages about it not working properly with Ubuntu

[http://www.google.ca/search?q=Stocks+screenlet&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a](http://www.google.ca/search?q=Stocks+screenlet&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a)

---

