---
title: "Programmatically updating a YAML config file"
date: 2007-09-18
forum: Programming Talk
---

### Post by mssever on 2007-09-18
I'm developing a daemon that reads its configuration from a YAML file. I would like to write a GUI configuration/control utility. My problem is this: If I write the updated configuration file using the YAML methods I'm familiar with, I'll lose the comments in the file, and the configuration items won't necessarily end up in a logical order (since YAML hashes are unordered). Is there a way I can write the config file with the comments I want and the hash keys in the order I want? Building up a YAML string and simply writing that seems rather inelegant.

My project is written in Ruby, but I'm willing to consider Python for the configurator if there's a major advantage to doing so.

---

### Post by pmasiar on 2007-09-18
[http://en.wikipedia.org/wiki/Yaml#Bindings](http://en.wikipedia.org/wiki/Yaml#Bindings) suggest 2 libraries for Python and just one for Ruby, so Python wins ;-)

Try to compare them, this includes evaluating the community, forum/mailing response time and tone.

Python does have ordered hashes, so if it is important for you, you can reimplemnet it yourself, and save the comments too. Read/parse/update a YAML file seems like a reasonable feature, nice to have.

But creating a GUI just to edit plain YAML file? I thought that whole point of YAML is, it is easy to read and write by humans, no need for excessive GUI tools to do that? That was the whole selling point IIRC, no? SciTE is excellent GUI to edit a plain text file for me :-)

Of course, unless your YAML is really very complex and has complex dependencies. But them you might be still better of to redesign the whore wretched thing first. Maybe split to sections, maybe some validator? GUI with human intervention should be not the first choice when handling complex problem, but the last.

---

### Post by mssever on 2007-09-18
> **pmasiar said:**
> [http://en.wikipedia.org/wiki/Yaml#Bindings](http://en.wikipedia.org/wiki/Yaml#Bindings) suggest 2 libraries for Python and just one for Ruby, so Python wins ;-)Thanks. It doesn't appear that any of those libraries support what I want. The YAML spec mentions using a stylesheet to influence YAML layout, but I haven't found anything in those libraries about a stylesheet. Maybe I will have to build up a string.
> Python does have ordered hashes, so if it is important for you, you can reimplemnet it yourself, and save the comments too. Read/parse/update a YAML file seems like a reasonable feature, nice to have.I've thought about that, but I'm not really interested in taking on such a project myself. It would take far too much time to justify the payoff.

> But creating a GUI just to edit plain YAML file? I thought that whole point of YAML is, it is easy to read and write by humans, no need for excessive GUI tools to do that? That was the whole selling point IIRC, no?Actually, the config is quite simple. Those of us who are experienced enough with Linux to know what to expect when it comes to configuration won't need a GUI. That's the main reason I used YAML in the first place. But a significant portion of my intended audience is unfamiliar with Linux ways, so I'd rather have a program that works both ways.

In addition, my program can't function as intended until it knows a certain amount of personal information--which can't be determined automatically. So configuration is essential. When it comes time to package it up in a deb, I'll want to use debconf to ask the user for the critical information. So I'll need the ability to generate a proper config file with or without a GUI.

---

### Post by pmasiar on 2007-09-18
Then your second best option is to parse  YAML file and output it using some templating system of your choice.

---

### Post by mssever on 2007-09-18
Good suggestion. Thanks.

---

