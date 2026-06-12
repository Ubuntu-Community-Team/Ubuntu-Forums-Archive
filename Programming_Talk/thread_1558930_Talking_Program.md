---
title: "Talking Program"
date: 2010-08-22
forum: Programming Talk
---

### Post by worksofcraft on 2010-08-22
I know this forum is for programming talk but I'm writing a talking program (A speaking clock in Python, which I'm learning as I go).

It is part of my research into internationalization... you see different languages build sentences in different order so one can't literally translate each audio file. It is my intention to use the gettext package to select and sequence translated audio fragments, but that's a little way off yet... 

So far I've created gstreamer objects to do the speaking but each fragment incurs a lot of overhead. What I want is a way to simply switch the selected input file and retain as much of the gstreamer pipeline as I can.

Can anyone help with experience, or ideas on how to do this efficiently?

---

### Post by worksofcraft on 2010-08-23
lol, I'm so dumb... I already was given the answer in example 2.3 of [http://pygstdocs.berlios.de/pygst-tutorial/playbin.html](http://pygstdocs.berlios.de/pygst-tutorial/playbin.html) and I even had modularized earlier into inheriting from a common AudioPlayer base class...

So my next step is the really hard one...
In English it has to say something like:

"at the 3rd beep it will be 40 5 minutes past 4", where 3rd, 40, 5 and 4 are all speech fragments that are selected based on program variables.

but in Dutch for instance, I gather it needs to say:

"bij de 3e fluit toon zal het 4 uur 5 en 40 zijn

so like a completely different sequence of the same variables and different arrangement of fixed sound bytes in between :shock:

Well you might be anticipating how the translator will have to make a format string consisting of sound file names to be played but meanwhile I really just don't know if there are languages out there that would need to differentiate on more than these 4 variables :(

So if anyone has any suggestions... I'm all ears, because I'll try to think of a solution before I get carried away with more coding ;)

p.s. I just realized that "tenty two" is not a good way to say twelve, so since similar may occur in different languages for different numbers I suppose the only universal way to do it is to have 59 separate sound files for all the minutes from 1 to 59

---

### Post by worksofcraft on 2010-08-23
The basic speech internationalization is very simple: a translatable format string that specifies the fixed audio files and takes as parameters two calls to dngettext(): One for the number of minutes and one for the hour.

Both these could have text domain _speaknumbers. The _speaknumbers domain would need no less than 60 plural forms: e.g. files 0.ogg to 59.ogg as translations of the word 'number.ogg'.

A third parameter can be an ordinary call to ngettext to pluralise the speech file selection for either 'minute' or 'minutes'.

However that does produce a fairly robotic sounding results like
"it will be zero minutes past nineteen".
From a format that looks like:
```

gettext("it_will_be {0} {2} past {1}").format(
	dngettext('_speaknumber', 'number.ogg', '', minute),
	dngettext('_speaknumber, 'number.ogg', '', hour)
	ngettext('minute.ogg', 'minutes.ogg', minute),
)

```
This might not be considered acceptable in some languages (including English).

I can easily improve that by having separate domains for the minutes and the hours and then substitute 'midday' and 'midnight' and make 13...23 map onto 1 to 11 pm in a _speakhour domain, but at the moment I'm having fun making my own gstreamer audio editor to produce all the sound clips :)

There is scope for taking it further still, perhaps saying 'half' instead of 30. Having zero come out as empty and similarly changing the word 'minutes' not just for one but also when 0 or 30. That again would not be good enough for some languages where once you get to half past they want to start saying how many minutes *to the next hour*!

Instead of specifying the text domain with a numeric lookup parameter it would be much more flexible to specify the domain with each parameter place holder in the format string itself. Then adding possibility of having the text domain selected on basis of another numeric parameter. Thus for instance to make it say the next hour when minute is > 30.

something like:
```

gettext("it will be {_speaknumber:0}{_pluraliseminute:0}{_to_past:0}{2:1}").format(
	minute, dngettext(_to_from,'_hour','_nexthour', minute), hour
)

```

You have to use your imagination to see what that would mean because I don't think Python can do this yet.
I am confident I could make a new format parsing function for C++ as I've done one in the past for Java when they didn't have yet, but I don't think I'll be taking this project quite that far :shock:

Anyway I hope I haven't bored you all to tears. I just like writing stuff I find interesting. IDK should I mark this one as solved then ?

---

### Post by shababhsiddique on 2010-08-23
Interesting work.. there is a thing called espeak in ubuntu.. if you are using it. go to terminal and type espeak "hello there" it will speak out ! so if your language supports system call you can simply pass the string to system and it will speak! i have made a chatter bot this way. It take a line thinks for a answer a little bit like ELIZA and gives it by speaking..

---

### Post by worksofcraft on 2010-08-23
> **shababhsiddique said:**
> Interesting work.. there is a thing called espeak in ubuntu... 

Hey that's a really good tip there shababhsiddique :)

It would be interesting to use espeak as a source in gstreamer, and I'll also be looking at how they organise their files for different languages.

Meanwhile, creating my _speaknumber domain went very easily and there were no problems creating 100 pluralized forms. I used Audacity to record and there are still a few bit's of excess silence to trim here and there.

Most entries could be composed by combining multiple files e.g. to pluralize for 98 the translation simply reads "90.ogg 8.ogg". The good thing is that my program can now potentially speak in many languages although there is absolutely *nothing* that is language dependent in the code: **It's all in the gettext domain!**

Thus in my French portable object file the translation entry for plural form 98 will read: "4.ogg 20.ogg 10.ogg 8.ogg" and in German it would be "8.ogg und.ogg 90.ogg"

Clearly all the .ogg's get a bit verbose so I'm going to algorithmically append file type suffix as well as prefixing a file path.

The latter needs to depend on selected locale. In analogy with the LC_MESSAGES of gettext, I'm thinking of adopting /usr/share/locale/xx_YY/speak/domain, or if the file isn't found there to look in /usr/share/locale/xx/speak/domain. i.e. for my application and locale, domain would be "_speaknumber", xx becomes "en" and yy is "NZ" for English New Zealand.

It's all good fun and seems much easier than I thought it would be :)

---

### Post by worksofcraft on 2010-08-24
Still a bit rough round the edges... but makes an impressive example of the flexibility in GNU gettext package!
This simple Python script puts numbers into speech includes all the audio to do English, French, Dutch, German and Italian and yet no code that is locale dependent even though it's building totally different locale dependent speech sequences dynamically.

I moved the archive to
[http://code.google.com/hosting/search?q=speaknumber&btn=Search+projects](http://code.google.com/hosting/search?q=speaknumber&btn=Search+projects)

---

### Post by worksofcraft on 2010-08-30
W00000t

Here is what someone who really knows about i18n and l10n had to say about my work :)

> 
Oh, this must be fun indeed :-) And it's quite usable for telephone
based services, or for speech-programmed devices.

Nitpicking: In _speak100.fr.po
msgstr[81] "4 40 et 1"  should be  "4 20 1"
msgstr[91] "4 20 et 11" should be  "4 20 11"

This is so original. It's worth making more public. I don't know how.
Maybe write about it in [email]translation-i18n@lists.sourceforge.net[/email],
or put a blog on [http://planet.gnome.org/](http://planet.gnome.org/) ?



So now I just have to work out how to blog there and hopefully other people can take this back to the future with them :)
re: > [http://code.google.com/hosting/search?q=speaknumber&btn=Search+projects](http://code.google.com/hosting/search?q=speaknumber&btn=Search+projects)

---

