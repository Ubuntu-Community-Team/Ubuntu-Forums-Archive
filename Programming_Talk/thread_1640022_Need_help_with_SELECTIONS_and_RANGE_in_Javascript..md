---
title: "Need help with SELECTIONS and RANGE in Javascript."
date: 2010-12-07
forum: Programming Talk
---

### Post by Krupski on 2010-12-07
Hi all,

First of all, [COLOR="Red"]I am not a student and this is not homework.[/COLOR] I'm posting here because you people are always helpful.

Anyway.........

I am trying to take a bulletin board software package (PHPBB3) and convert the plain textarea editor to a full WYSIWYG editor.

I've done this using TinyMCE and everything is working well except for one stumbling block...

I'm trying to also support the legacy BBCode system (because PHPBB allows the admin to add and define new, custom BBCodes).

The basic idea is this: Let's say I want to wrap "[bbcode]" around a selection. What should happen is this:

(1) Select the area to surround ("the_selection")
(2) Change it to "[bbcode]the_selection[/bbcode]"
(3) Select (or re-select) "the_selection".

Or, if nothing is selected, I should get this:

[bbcode]**|**[/bbcode] (the pipe symbolizes the cursor).

I've been searching Google and reading books for weeks, beating my head against the wall. I've posted my question on the TinyMCE "support" forum, which is 110% useless.

All I know is, what I want to do has something to do with "DOM range".

I also need to be able to find where the start and end points of things are, and move the cursor if necessary.

One problem is, all web examples fail to work because TinyMCE has it's own DOM interface. For example, instead of "createRange()", the editor uses "creatRng()" to create a range INSIDE the editor itself.

Here is a piece of diagnostic code I wrote in Javascript to at least try to learn what the heck is going on... but I'm still stumped:

```

var ed = tinyMCE.activeEditor;
var sel = ed.selection;
var node = sel.getNode();
var rng = sel.getRng();
var sc = rng.startContainer;
var ec = rng.endContainer;
var sofs = rng.startOffset;
var eofs = rng.endOffset;

var str = '';

str += 'ed: ' + ed + '\n';
str += 'sel: ' + sel + '\n';
str += 'node: ' + node + '\n';
str += 'range: ' + rng + '\n';
str += 'range.startContainer.data: ' + sc.data + '\n';
str += 'range.startContainer.length: ' + sc.length + '\n';
str += 'range.startOffset: ' + sofs + '\n';
str += 'range.endContainer.data: ' + ec.data + '\n';
str += 'range.endContainer.length: ' + ec.length + '\n';
str += 'range.endOffset: ' + eofs + '\n';

alert(str);

```

Running the above results in this:

[img]http://three-dog.homelinux.com/phpbb/images/selection.jpg[/img]

Can anyone give me a hint as to how to do what I'm trying to do?

Just a few lines of code, or pseudo code or a short explanation as to what exactly a "range" is... just so I get the basic idea, is all I need.

Thanks in advance!

-- Roger

---

### Post by Reiger on 2010-12-07
Not sure what the problem is, but two things:

(1) You can already obtain explicit (string?) indices where the selection/range appears to start and end, so you might want to start from there.
(2) JavaScript objects can be introspected, so if you have proper (not obfuscated) source code debugging like this may prove useful:
```

var str="";
for(var m in obj) { str+= ("obj."+m+"="+typeof(obj[m])+"\n"); }
alert(str);

```

---

### Post by Krupski on 2010-12-07
> **Reiger said:**
> Not sure what the problem is, but two things:

(1) You can already obtain explicit (string?) indices where the selection/range appears to start and end, so you might want to start from there.
(2) JavaScript objects can be introspected, so if you have proper (not obfuscated) source code debugging like this may prove useful:
```

var str="";
for(var m in obj) { str+= ("obj."+m+"="+typeof(obj[m])+"\n"); }
alert(str);

```

OMG!!!!!! That little piece of code shows me EVERYTHING that any object can do!!!

```

for (var n = 0; n < 1e6; n++)
{
    alert('THANK YOU!!!');
}

```

I think I'm going to be able to extract enough information out now to get this figured out.

Awesome... absolutely awesome! THANK YOU!

-- Roger

---

### Post by myrtle1908 on 2010-12-07
See this thread ... 

Surprisingly the OP was involved in this discussion :)

[http://ubuntuforums.org/showthread.php?t=1512707&highlight=javascript+selection&page=2](http://ubuntuforums.org/showthread.php?t=1512707&highlight=javascript+selection&page=2)

---

