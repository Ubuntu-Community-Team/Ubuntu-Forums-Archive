---
title: "RegExp voodoo"
date: 2006-03-31
forum: Programming Talk
---

### Post by rosslaird on 2006-03-31
My mind must be mush, because I've been trying to figure this out for hours, with no appreciable results. What I want is very simple:

In Vim (or Kate), I need to replace html entities that are missing the closing semicolon with entities that have the semicolon. All I need to do is add the semicolon onto the ends of entities such as these:

&#8211
&#8212
&#8217

So, I need to search for &#82[plus variable two digits] and replace with &#82[variable two digits];

This should be really easy, but these regular expressions are beyond me.

Help would be really good at this point.

Ross

---

### Post by hod139 on 2006-03-31
Not well tested, but I think something like this:
```

sed -i.bak 's/&#82..$/&;/' foo

```

---

### Post by xenmax on 2006-03-31
In vim, you try this substitution:
```
s/\(&#82[0-9][0-9]\)$/\1;/
```

The \(..\) is to remember what was matched and it will be stored in \1 for first occurence and so on ...

PS: Just saw hod139's post. You can try that - looks much sleeker code :)

---

### Post by rosslaird on 2006-03-31
Unless I've done this incorrectly... it did not work.

I made a test.txt file, then entered your command from the command line:

sed -i.bak 's/&#82..$/&;/' test.txt

No changes were made to the html entities.

Also, I'd like to be able to do this in vim, because the documents I'm working on are not stand-alone files but table entries in a mysql database. I can copy them, paste into vim, correct, and paste back fairly easily; but if I have to save each of them as a separate file then I have an extra step.

Ross

---

### Post by rosslaird on 2006-03-31
xenmax:

Looks like our posts crossed. Thanks for the vim suggestion. I entered it exactly as shown (twice, to be sure). and both times I got "Pattern not found."

Hm.

---

### Post by xenmax on 2006-03-31
Hmm... I tried it in vim and it works for me. Can you post a sample line of your file if it is ok to do so?

---

### Post by rosslaird on 2006-03-31
Sure, here's some text:

```
<p>I stand in the great hall of the <a href="http://www.moa.ubc.ca/">Museum of Anthropology</a> in Vancouver, head bent back, gazing up forty feet to where precise images have been carved into cedar totem poles by craftsmen whose art has been almost entirely erased by time. This museum possesses one of the finest collections of carved wood artifacts in the world, and I feel quite at home here. Near the bottom of a nearby pole, a smooth shouldered wolf rests in the shadow of a killer whale. The eye of the whale is a shadowed well. This wood, these bones, trace the nature and purpose of a vast awareness, a living spirit in the grain, each knot and every growth ring a secret hieroglyph worked carefully into many layers of meaning. The echo of leaves is here, the resonance of damp fields half submerged in twilight, of dark soil and tales of night. And long, interwoven strands of time knitted together by wood and human hands. The wood has been coaxed into shape &#8211 whittled, chiseled, sculpted with broad, incising strokes &#8211 by tools of utmost antiquity, by weapons, by stones, by meteors, by fragments of ships: countless forms oiled by luminous skin.</p>

<p>Although the focus of the collections is northwestern &#8211; hundreds of examples &#8211 I also find works from Indonesia and Greenland and China, specimens of all kinds and of diverse ages: an eagle with a five-foot, intricately carved beak, a tenebrous skull shape, moons and ravens and wild spirits of the forest. There are objects of great power here, and I am daunted by the virtuosity of craftsmanship displayed in so many of them. But as I gaze at these ethereal faces staring back from a lost age, their muted colors hiding a secret flame, once again I hear that whisper spiraling out from the primordial source of things.</p>

```

Sometimes, in vim, when I've been trying variations of what you posted (over the last several hours...), it seems to correct half of the entities, but leave some out. And I can't figure out the pattern of what it's skipping. But the above example returns "Pattern not found" (I just tried again).

---

### Post by xenmax on 2006-03-31
Both hod139's and my solution assume that the line ends with &#82[][] (the $ indicates end of line)
If it is not, then you need to remove the $ in regexp. But then, substitution will kick in anywhere on line that matches your pattern, but will substitute only first such pattern, unless you provide "/g" modifier to make it global s n r [global as in all matching patterns on line are substituted]

---

### Post by rosslaird on 2006-03-31
[QUOTE=xenmax]Both hod139's and my solution assume that the line ends with &#82[][] (the $ indicates end of line)[/QUOTE]

OK -- well, as you can see, most of the entitities are not at the ends of the lines.

[QUOTE=xenmax]If it is not, then you need to remove the $ in regexp. But then, substitution will kick in anywhere on line that matches your pattern, but will substitute only first such pattern, unless you provide "/g" modifier to make it global s n r [global as in all matching patterns on line are substituted][/QUOTE]

Aha! That's what's been happening. I thought it might have been getting just the first one on the line and skipping the others.

Taking out the $ and adding in /g works!

Now, my last task is to put this into a macro or something so that I can just hit a key rather than entering the expression over and over again for every entry in my database table. I've never made a vim macro, but I think I'll be able to figure it out (tips always appreciated, though).

Thanks very much.

Ross

---

