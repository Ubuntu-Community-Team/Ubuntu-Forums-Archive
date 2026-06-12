---
title: "Keyboard layout annoying"
date: 2018-10-14
forum: New to Ubuntu
---

### Post by stumpie2 on 2018-10-14
Hi all,

I'm having trouble figuring out what keyboard layout works for me. Currently I'm using English (US, International with dead keys). In Windows with US International I'm used to type ' followed by t to get 't. In Ubuntu this sequence returns absolutely nothing. I need to hit ' space t to get the same result which simply breaks any typing speed I have. As I'm using Dutch and English in equal amounts, this is quite annoying. As my primary language is Dutch that frequently uses characters like é or ü or ë and € switching to a full US keyboard doesn't seem to be an option.

Just think of how many times I'm writing "can" in stead of "can't" which is confusing for anyone reading my emails...I've been digging around on the web and the forum search and I've found quite a bunch of questions being asked before but no answers. I'd (had to type that three times to get it right...) really appreciate your thought on this one.

Currently running Ubuntu Gnome 16.04 LTS

Thanks,

Coen

---

### Post by Impavidus on 2018-10-15
Hello, I'm dutch too.

The sequence <dead acute> t is supposed to generate a t with an acute accent, but such a character doesn't exist. Windows replaces it automatically with 't, but Ubuntu ignores it. I've tried US International with dead keys, but didn't like it. It makes it harder to type an apostrophe. In dutch, you need the apostrophe very often, but the accented character are relatively rare. And when using dead keys, we risk typing zo&#324; instead of zo'n (for non-dutch readers, zo'n ("such a") is one of the most common words in dutch). I'm sure you've seen it happen.

I use the US keyboard with Euro-sign on 5, so I can type AltGr+5 to get €. I also configured the compose key ("samensteltoets") on the left Windows key, but you can use a different one for that. That way I can type the ', ", ~ etc. by hitting a single key, and type the accented characters with <compose> <accent> <letter>. For example, <compose> ' e gives é, <compose> " u gives ü. That should be good enough for dutch or occasionally typing french or german.

I do most of my pretty typing in LaTeX with the dutch babel package, which allows a shortcut for the trema. Just "e will produce ë. Even better, it's smart enough to remove the trema if the word is hyphenated just before this character: zee"en is rendered zeeën or zee-en, depending on where line gets broken.

---

### Post by stumpie2 on 2018-10-18
Thanks for this! It seems the implementation is 100% consistent but a little inconsistency would make life a bit easier. I've found out in the meantime that hitting the apostrophe twice returns what I need, but it's not really what I like. I've switched to US with Euro on 5 to see if this works better for me. in English it seems to work out fine, don't know what happens in Dutch yet. Now I need to figure out how to set a compose key, didn't get it to work yet. I've foud the configuration dialog, but I haven't found how to set my preference yet.

---

### Post by Impavidus on 2018-10-18
Those GUIs for system config are highly variable between different versions and flavours of Ubuntu. I'm on Xubuntu 18.04, so on my system the option for the compose key is probably somewhere else than on your system. It should be somewhere in your keyboard settings.

---

