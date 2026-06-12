---
title: "I can't understand what this javascript code does"
date: 2014-01-06
forum: Programming Talk
---

### Post by SledgeHammer_999 on 2014-01-06
Hi,

I know C++ pretty well, but I am a total noob in javascript. I was reading a piece of code and trying to understand it. Hopefully the javascript syntax is pretty close to the C++ one so I didn't have much trouble figuring out what is happening. However, I came across a line of code that although I think I understand what it does, I can't find any online reference/documentation on the method/function used.

I'll try to give it summarised:
[php]
function(id, row, status){
var td = new Element('td');
blah blah
td.set('html', row[i]);
}
[/php]

My question is what is this "set()" method used on the last line? (I won't state what I think is happening).

If you want more context about the actual code see here: [https://github.com/qbittorrent/qBittorrent/blob/master/src/webui/scripts/dynamicTable.js#L251](https://github.com/qbittorrent/qBittorrent/blob/master/src/webui/scripts/dynamicTable.js#L251)
(line 251)

Thanks, in advance.

---

### Post by Dave_L on 2014-01-06
Is Element a standard Javascript class, or a custom class?  I'm pretty rusty on Javascript.

---

### Post by SledgeHammer_999 on 2014-01-07
> **Dave_L said:**
> Is Element a standard Javascript class, or a custom class?  I'm pretty rusty on Javascript.

Thanks for the hint. First I thought that Element refered to a DOM Element but actually is mootools' Element class.
Direct link to the set() method: [http://mootools.net/docs/core/Element/Element#Element:set](http://mootools.net/docs/core/Element/Element#Element:set)

[rant]That's why I don't like languages that don't enforce you to declare the type of a variable.[/rant]

---

