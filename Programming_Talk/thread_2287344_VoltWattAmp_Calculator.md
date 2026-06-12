---
title: "Volt/Watt/Amp Calculator"
date: 2015-07-18
forum: Programming Talk
---

### Post by gerowen on 2015-07-18
I wrote this mainly just as an exercise for myself, but also as a tool to quickly figure out how much of a load a particular power source can handle, or how big a power source I need to run a particular device, whether that be one of my CB radios, a sound system, etc.
 
Anyway, I just thought I would share it with you guys in case somebody finds it useful.  I know there's websites that do the same thing, but I wrote it as an exercise for myself and thought I'd share it, and also because sometimes I'm out at somebody else's house with no internet or cell phone service, and it'd be nifty to be able to use this little program in conjunction with my multimeter to do some quick calculations.
 
Note: It is a python file, so you have to have Python 3 installed to run it (will probably work under Python 2 if you just delete Line 1 that specifies Python 3), and if you also happen to have the colorama library installed it'll highlight the desired output in green for you.  Colorama is available in the Ubuntu package manager, or from their website. (URL is in the program)  Should be cross platform across Linux, Windows, OSX, pretty much anything you can put Python on.

Link: [https://dl.dropboxusercontent.com/u/6017319/Scripts/powercalc.py](https://dl.dropboxusercontent.com/u/6017319/Scripts/powercalc.py)

Screenshot
[ATTACH=CONFIG]263272[/ATTACH]

I'm thinking about updating it to add calculations for impedance, and maybe a quick GUI using something easy like easygui, but for right now this will suffice just fine for me.

---

### Post by trent.josephsen on 2015-07-19
Cool. You might consider using the [decimal module]("https://docs.python.org/3/library/decimal.html") from the standard library instead of converting between floats and strings. Decimal arithmetic is almost universally better for anything user-facing.

It's a bit annoying to have to "Press Enter to continue" all the time. For the colorama error, a single line saying that colorama is not installed and output highlighting is disabled will suffice; you don't need to get the user's consent to continue. Similarly, at the end of the main while loop, you don't need to wait for the user to hit Enter: just say "try again" and let the loop continue. As a rule, you probably shouldn't ever call input() unless you do something with the result.

Nitpick: I wish you (and people in general) wouldn't refer to power and current as "wattage" and "amperage". Okay, so "electric potential" is a mouthful and there's no really good term for what volts measure, so "voltage" gets a pass. But we don't measure the *inchage* of phone screens, the *ounceage* of drinks, the *poundage* of people, or the *dollarage* of anything (apologies to non-Americans); we use generic terms: length, volume, weight, cost. In many cases the "-age" construction means something different than the generic term, as with footage, mileage, tonnage. In fact, we see this also with wattage and amperage, where they're often used to describe the *rating* of a device as distinct from the measurement itself:
> PAT. What's the **wattage** of this microwave, Mike?
MIKE. One thousand fifty watts.
PAT. Wow! That's a lot of **power**.
Maybe most of the time you're dealing with ratings and not measurements. But the script you've written is a general tool, so if I were writing it, I'd use the general term (current/power) and not the specific one (amperage/wattage).
*This public service announcement brought to you by Peeved Engineers and Developers Against Nonmeaningful Terminology.*

---

