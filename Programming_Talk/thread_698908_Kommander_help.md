---
title: "Kommander help"
date: 2008-02-16
forum: Programming Talk
---

### Post by SergeiFranco on 2008-02-16
Right, I am using Kommander to build a small project of mine, it is basically a front end for Amarok that controls it via DCOP.
I have posted the original help post in amarok forum but I think this forum is more likely to result in a solution so here is the link:
[http://amarok.kde.org/forum/index.php/topic,14864.msg21740.html#msg21740](http://amarok.kde.org/forum/index.php/topic,14864.msg21740.html#msg21740)
and contents:
Help!
I am trying to make Equalizer work with my front-end that I have made with Kommander,  I get two problems:
1) if I try to use built in dcop function for example:
```

@Array.setValue(eq,0,@expr(@expr(100-@Gain.text)*2-100))
@Array.setValue(eq,1,@expr(@expr(100-@band30hz.text)*2-100))
@Array.setValue(eq,2,@expr(@expr(100-@band60hz.text)*2-100))
@Array.setValue(eq,3,@expr(@expr(100-@band125hz.text)*2-100))
@Array.setValue(eq,4,@expr(@expr(100-@band250hz.text)*2-100))
@Array.setValue(eq,5,@expr(@expr(100-@band500hz.text)*2-100))
@Array.setValue(eq,6,@expr(@expr(100-@band1khz.text)*2-100))
@Array.setValue(eq,7,@expr(@expr(100-@band2khz.text)*2-100))
@Array.setValue(eq,8,@expr(@expr(100-@band4khz.text)*2-100))
@Array.setValue(eq,9,@expr(@expr(100-@band8khz.text)*2-100))
@Array.setValue(eq,10,@expr(@expr(100-@band16khz.text)*2-100))

@@dcop(amarok, player, setEqualizer(int,int,int,int,int,int,int,int,int,int,int), @Array.value(eq,0), @Array.value(eq,1), @Array.value(eq,2), @Array.value(eq,3), @Array.value(eq,4), @Array.value(eq,5), @Array.value(eq,6), @Array.value(eq,7), @Array.value(eq,8), @Array.value(eq,9), @Array.value(eq,10))
```
Which supposed to transform the value from apropriate slider to value that Amarok equalizer accepts. But this does not work (it complains about number of arguments).
I also have tried to pass it as QString:
```
@Label57.setText(@Array.value(eq,0) @Array.value(eq,1) @Array.value(eq,2) @Array.value(eq,3) @Array.value(eq,4) @Array.value(eq,5) @Array.value(eq,6) @Array.value(eq,7) @Array.value(eq,8) @Array.value(eq,9) @Array.value(eq,10))
@dcop(amarok, player, setEqualizer(QString), @Label57.text)
``` With Label57 displaying the values properly, but it says it failed to perform DCOP call.

if I issue call from cli it works:
```
dcop amarok player setEqualizer 100 100 100 100 100 100 100 100 100 100 100
```
so I have decided to use @exec feature
```
@Label57.setText(@Array.value(eq,0) @Array.value(eq,1) @Array.value(eq,2) @Array.value(eq,3) @Array.value(eq,4) @Array.value(eq,5) @Array.value(eq,6) @Array.value(eq,7) @Array.value(eq,8) @Array.value(eq,9) @Array.value(eq,10))
@exec(dcop amarok player setEqualizer @Label57.text)
```
I used the Label57 as temp value as it was already defined, but it behaves exactly the same if I use all the array values in the @exec call. This method "works"...
which brings me to another problem:
When it works, if I click on the slider that is connected to a script widget (ValueChanged->populate) that contains the DCOP call to amarok to change equalizer settings, the slider starts either going up or down by itself until it reaches maximum(or minimum), at first I though my scroll wheel was stuck but that was not the case... I have no idea why is this happening, I have nothing else that should affect the sliders in such way that it would move them (I have nothing that writes to sliders text field). I have a suspicion that this is a bug in kommander and ValueChange(int) is getting fed back into slider somehow making it move...I do not like to use SliderPressed/Released signals as they are not affecting the values passed to the equalizer instantly and sometime require multiple clicks to work (move release, click, other wise it will not update).
My other sliders that use ValueChange signal work fine...
I am very close on finishing this script, it is very frustrating to be stuck and have no idea on what to do next...

I am attaching my kommander file(zipped), I have connected 30hz slider ValueChanged signal to script object, while 60hz slider is connected to SliderPressed, 125hz to SliderReleased, and 250Hz to both pressed/released....






Thanks.

Sergei.

---

### Post by SergeiFranco on 2008-02-16
Little bit of digging leads to this:
[http://mail.kdewebdev.org/pipermail/kommander/2007-February/001557.html](http://mail.kdewebdev.org/pipermail/kommander/2007-February/001557.html)

So I guess it is a bug... is there anyway to work around it?

Also, default QT slider has got very, very annoying behaviour:
if you click anywhere on the slider it will NOT jump to that location but will increment towards it.
Is it possible to somehow make it work properly?

---

### Post by SergeiFranco on 2008-02-20
I was trying to work around the issue by doing the following:
the sliders do not emit any signals, the timer does (every 100ms), when timer emits the signal, it is connected to a script object that reads the values of each slider, recalculates it, and then outputs to amarok.
The not very funny thing is that sliders still move by themselves when clicked on. Very annoying feature.
Will try to experiment some more.

---

### Post by SergeiFranco on 2008-02-20
I have narrowed down to what part of the code causing self moving sliders:
```
@exec(dcop amarok player setEqualizer @Array.value(eq,0) @Array.value(eq,1) @Array.value(eq,2) @Array.value(eq,3) @Array.value(eq,4) @Array.value(eq,5) @Array.value(eq,6) @Array.value(eq,7) @Array.value(eq,8) @Array.value(eq,9) @Array.value(eq,10))
```
for 1 thing I don't understand how this line of code has to do with sliders, if it does not deal with them directly?

I am resorting to @exec in first place because for some reason ```
@dcop(amarok, player, setEqualizer(int, int, int, int, int, int, int, int, int, int, int), @Array.value(eq,0), @Array.value(eq,1), @Array.value(eq,2), @Array.value(eq,3), @Array.value(eq,4), @Array.value(eq,5), @Array.value(eq,6), @Array.value(eq,7), @Array.value(eq,8), @Array.value(eq,9), @Array.value(eq,10)) 
```
does not work (probably due to limit how many arguments can @dcop pass)...

---

### Post by SergeiFranco on 2008-02-20
to make sure that it does not complain about arrays I have tried this:
```
@dcop(amarok, player, "setEqualizer(int,int,int,int,int,int,int,int,int,int,int)", 33, 33, 33, 33, 33, 33, 33, 33, 33, 33, 33)
```

and it complains about number of arguments....

and this:
```
@exec(dcop amarok player setEqualizer 33 33 33 33 33 33 33 33 33 33 33)
```
still causes sliders to self move...
WTF is going on there?

UPDATE: having anything in @exec will cause sliders to move!!!! (like @exec(ls) @exec(uname) etc.)

How do I contact Kommander developers to let them know of this bug?

---

### Post by ftso on 2008-03-05
hi, i post in this thread because i need some help for kommander.

How can i test if a file exist with kommander's if ?


with shell i can this with that code
```
if (test -e /tmp/kgrtv_3); then
echo sile exists
fi
```


but how can test if file exists with @if

i want something like that:

```
@if (test -e /tmp/kgrtv_3) //this is false
@ScriptObject6.execute
@endif
```

thanks for any help.

*sorry for my bad english*

---

