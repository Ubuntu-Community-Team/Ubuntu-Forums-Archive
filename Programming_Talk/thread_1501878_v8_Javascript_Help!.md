---
title: "v8 Javascript Help!"
date: 2010-06-04
forum: Programming Talk
---

### Post by ctult on 2010-06-04
Hi,
I would like to know where I could get some good tutorials for v8/Spidermonkey/Rhino javascript engines, but I can't seem to find any.  Also, I would like to know if there is an import function. 

Thanks in advance,
CTuLT

P.S. Could someone please answer?

---

### Post by Unterseeboot_234 on 2010-06-23
Your question is kinda vague, but if you're still looking...

Rhino is the javascript engine that comes with Java6, released 2006. For a general intro see:

**[O'Reilly's -- OnJava, Mustang meets the Rhino]("http://onjava.com/pub/a/onjava/2006/04/26/mustang-meets-rhino-java-se-6-scripting.html")**

If you are coding from the java end of the telescope:
import javax.script.ScriptEngineManager;

SpiderMonkey is an add-on bin. It can do many things, including Command-Line-Interface just like perl

$ js -e 'print("hello, world");'

If you view the JSEngine-SpiderMonkey as another interpreter, then you see that SpiderMonkey is just another engine with the biggest gain being functionality with I/O. If you don't want to use java... python, and perl or bash shell can also make calls to spidermonkey-bin (available as Synaptic, or sudo apt-get install spidermonkey-bin. To use perl...

**[perl module]("http://search.cpan.org/~mschilli/JavaScript-SpiderMonkey-0.12/SpiderMonkey.pm#SpiderMonkey_Installation")**

for basic CLI after you installed spidermonkey...
**[google groups West End Linux Users]("http://groups.google.com/group/cwelug/browse_thread/thread/c325a6c1e9287ae5")**

---

