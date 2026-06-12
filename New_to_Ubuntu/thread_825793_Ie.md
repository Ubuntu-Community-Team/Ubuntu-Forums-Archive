---
title: "Ie??"
date: 2008-06-11
forum: New to Ubuntu
---

### Post by bkamalnivas on 2008-06-11
internet explorer in ubuntu??
is it possible...
please help

---

### Post by robertchahine on 2008-06-11
i think you can run it via wine.
but when you have mozilla firefox, why to use Ie (with my respect)?

---

### Post by robertchahine on 2008-06-11
oh, you're new to the forums , welcome.
if you don't know what is wine, it's a software.
go to the application pannel>accessories>terminal
the write this code
```

sudo apt-get install wine 
```

then open the setup with wine emulator

---

### Post by bkamalnivas on 2008-06-11
dats rite..but my internet account can be viewed ony in IE

---

### Post by kk0sse54 on 2008-06-11
Instead of going through all the trouble of getting it to work in wine why not just use firefox or one of the countless other options?
Edit: nevermind I understand now.....

---

### Post by Joeb454 on 2008-06-11
What internet account?

I've not come across many websites nowadays that are IE only

---

### Post by bkamalnivas on 2008-06-11
thanxx a lot

---

### Post by Fedz on 2008-06-11
Just put firefox on and if really needed put the firefox add-on 'user agent swithcher' and make the site think you're using IE.

If that's the case complain to the site owner ;-)

I doubt IE runs in Wine via ubuntu as IE has a dependency on many files that maybe not installed with Wine alone.

---

### Post by Joeb454 on 2008-06-11
Actually - it does work, check out [IEs4Linux]("http://www.tatanka.com.br/ies4linux/page/Main_Page")

---

### Post by robertchahine on 2008-06-11
> **Fedz said:**
> Just put firefox on and if really needed put the firefox add-on 'user agent swithcher' and make the site think you're using IE.

If that's the case complain to the site owner ;-)

I doubt IE runs in Wine via ubuntu as IE has a dependency on many files that maybe not installed with Wine alone.
well, i searched the wine database. and yep, IE can works under wine.
check this [http://appdb.winehq.org/search_results.php?cx=013271970634691685804%3Abc-56dvxydi&cof=FORID%3A11&q=internet+explorer&sa=Search#954](http://appdb.winehq.org/search_results.php?cx=013271970634691685804%3Abc-56dvxydi&cof=FORID%3A11&q=internet+explorer&sa=Search#954)

---

### Post by dje on 2008-06-11
As mentioned earlier you should try the [user agent switcher addon]("https://addons.mozilla.org/en-US/firefox/addon/59") for firefox before trying ies4linux. It's a much better solution and it even says on the ies4linux website that you shouldn't use internet explorer in wine for browsing (the ies4linux project is meant for web developers so they can test websites on internet explorer without windows)

dje

---

### Post by Fedz on 2008-06-11
I stand corrected - thanks :-D

The above does install the extra dependancies required for IE that aren't by default in the Wine install ;-)

---

### Post by robertchahine on 2008-06-11
you're welcome :D

---

### Post by SunnyRabbiera on 2008-06-11
> **bkamalnivas said:**
> dats rite..but my internet account can be viewed ony in IE

Who provides your service?

---

