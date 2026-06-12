---
title: "Firefox showing weird ? instead of correct symbol"
date: 2008-05-05
forum: New to Ubuntu
---

### Post by styphon on 2008-05-05
OK, I've finally decided to post here as this is driving me nuts. On some web pages I get weird question marks instead of the correct symbols. I think it's a problem within Firefox. The example page (where this is really prominent) is [http://checkmated.com/story.php?story=10117](http://checkmated.com/story.php?story=10117)

The source code of the page, that I get on Firefox is:
```
<p>&#65533;You really didn&#65533;t have to get me anything,&#65533; Harry repeated.</p>

<p>&#65533;Oh, yeah? Because I was going to return this if you didn&#65533;t want it,&#65533; quipped Ginny, hand clasped in his as she pulled him through the house towards the back garden.</p>

<p>He raised an eyebrow. &#65533;I&#65533;ve already got season tickets to all of your games, a flat in London, a Ministry job &#65533;&#65533;</p>

<p>&#65533;Fame, fortune, me &#65533; I know. There isn&#65533;t much to give the wizard who already has everything.&#65533; Grinning impishly, she came to a dead stop in the kitchen doorway and turned to face him before tilting her face upwards for a kiss, which he gave more than obligingly. Another followed. And, for a handful of long moments, the gift was forgotten.</p>

<p>Finally, she placed both hands on his chest and pushed back. </p>

<p>&#65533;It took me months to prepare, so I hope you do me the favor of being a gentleman and tell me how wonderful it is, even if you don&#65533;t want it.&#65533;</p>

<p>&#65533;Since when am I not a gentleman?&#65533; he asked with mock incredulity.</p>

<p>&#65533;You should be thankful you&#65533;re so bloody good-looking,&#65533; she teased, gripping the lapels of his shirt to pull him closer, &#65533;or you&#65533;d be a right insufferable prat.&#65533;</p>

<p>Heaving an exaggeratedly loud sigh he said, &#65533;I do tend to have that general impression on people.&#65533;</p>

<p>&#65533;Now shut your eyes. And no peeking, Potter, or I shall have to punish you,&#65533; Ginny ordered, adopting a serious tone. At his lifting an eyelid a fraction, she playfully swiped his rear with the cotton handkerchief she&#65533;d conjured with her wand before securing it over his eyes.</p>

<p>&#65533;Wait here,&#65533; she whispered in his ear.&#65533;&#65533; </p>

<p>Throwing open the door and racing halfway down the lawn, she stopped to yank the tarp off for the last time, heart battering almost painfully against her ribcage in thrilled anticipation while she gave everything a final once-over. Satisfied, she smiled and inhaled, steadying herself before sliding onto the leather seat.</p>

<p>&#65533;Can I look now?&#65533; Stepping onto the front stoop, Harry lifted a hand to finger the bottom of the blindfold.</p>

<p>&#65533;All right!&#65533; You can look,&#65533; she called, stretching her long legs before her.</p>

<p>During the next few seconds, she shifted slightly, squinting to see him raise a hand to his forehead in order to shield his eyes from the sunlight and make half a sweep of the back garden with his gaze before &#65533; <i>ah</i>.&#65533;&#65533; Even from that distance, she could see every line in his lean body tense with recognition.</p>

<p>And, just as quickly as she had become giddy with expectation, anxious uncertainty dripped over her like hot wax when she could not gauge from his reaction what he was feeling. Perhaps she had been mistaken, she thought in panic as he slowly ambled down the grassy slope, eyes bright, until he stood in front of her.</p>

<p>&#65533;It's yours now, if you want it,&#65533; she said carefully, studying his expression more closely as he trailed a hand down the side of Sirius&#65533;s motorbike until he reached her knee.</p>

<p>He swallowed thickly, pausing for a beat before replying quietly, &quot;I &#65533; yeah.&#65533;&#65533; Yeah, I think I do.&quot;</p>
```

Now, from what I see there a couple of times it loads the &quot; command correctly, but the majority of the time it just comes up with &#65533;.

I have tried changing the font, forcing it to use my font, changing to Unicode-8 and Unicode-15, Western ISO-8859-1 and 15. Still no joy.

Please help as this is driving me nuts.

---

### Post by styphon on 2008-05-06
OK, I've managed to solve this one myself. I'm not 100% sure what was doing it but I noticed that in Windows XP it wasn't doing it so I coppied the Character settings from there:
[LIST]
[*]Proportional: Serif
[*]Size: 16
[*]Serif: Times New Roman
[*]Sans-Serif: Arial
[*]Monospace: Courier New
[*]Size: 13
[*]Allow pages to choose their own fonts: True
[*]Default Character Coding: Western (ISO-8859-1)
[/LIST]

Hope this helps anyone suffering the same problem.

NOTE: To get the Times New Roman and Arial fonts install the Restricted Drivers from within Synaptic (Or Add/Remove Packages for the real newbies).

---

