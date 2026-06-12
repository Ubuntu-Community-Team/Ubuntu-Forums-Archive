---
title: "Ruby on Rails IDE"
date: 2007-09-28
forum: Programming Talk
---

### Post by codeking on 2007-09-28
Anyone know a good IDE for Ruby on Rails?  I've tried installing JEdit, but that starts loading then quits, and I cannot figure out how to install aptana.

---

### Post by exile on 2007-09-28
I used to use RadRails/Eclipse but recently I have installed the NetBeans 6beta for Ruby and I have found it to be really, really good. SVN + MySQL plugins make using it a charm.


See: [http://www.adaruby.com/2007/09/19/ruby-on-rails-developers-ide-netbeans-6-beta-1-is-out/]("http://www.adaruby.com/2007/09/19/ruby-on-rails-developers-ide-netbeans-6-beta-1-is-out/")

---

### Post by pmasiar on 2007-09-28
Dynamically typed languages like Ruby cannot have type-aware IDE like Statically typed languages do, and if you think about it for a minute you will understand why :-)

Also, new hot languages don't have as many IDEs as old boring ones. Most people just use their favorite programmer's plain text editor, my favorite is SciTE.

Edit: so someone made Eclipse plugin for Ruby. Does it mean Ruby becomes boring, too? :twisted:

---

### Post by loell on 2007-09-28
> **pmasiar said:**
> Dynamically typed languages like Ruby cannot have type-aware IDE like Statically typed languages do, and if you think about it for a minute you will understand why :-)

what about komodo IDE? ;) though a commercial app, it is designed for dynamically typed language.

---

### Post by pmasiar on 2007-09-28
I am aware about Komodo. There is also WingIDE and others.

But even if commercial, they cannot go around the fact that type information is known only at runtime. So you cannot have "intelliSense"-style method suggestion after you typed variablename-dot. Because you need to know type (class) to suggest methods, and I don't see any way around it. Do you?

---

### Post by loell on 2007-09-28
> **pmasiar said:**
> I am aware about Komodo. There is also WingIDE and others.

But even if commercial, they cannot go around the fact that type information is known only at runtime. So you cannot have "intelliSense"-style method suggestion after you typed variablename-dot. Because you need to know type (class) to suggest methods, and I don't see any way around it. Do you?

I'm using it right now, in windows though. 

yes there is intellisense when you type variablename-dot

---

### Post by kknd on 2007-09-28
Netbeans 6 does miracles for Ruby / JRuby.

---

### Post by skeeterbug on 2007-09-28
> **loell said:**
> I'm using it right now, in windows though. 

yes there is intellisense when you type variablename-dot

I use PyDev (Eclipse plugin for Python), and it has intellisense as well. It doesn't work nearly as good as it does for statically typed languages though. So in a way I would have to agree with pmasiar on this one.

---

### Post by fng on 2007-09-28
APTANA
[http://www.aptana.org/](http://www.aptana.org/)

It's a fork of eclipse 3.2 especially orientated at web development.
With the radrails plugin, it also has ruby on rails support.

---

### Post by loell on 2007-09-28
> **skeeterbug said:**
> I use PyDev (Eclipse plugin for Python), and it has intellisense as well. It doesn't work nearly as good as it does for statically typed languages though. So in a way I would have to agree with pmasiar on this one.

you would have to agree on what? ;)

 you did say that pydev eclipse has intellisense , though it doesn't good as statically typed language. 

so in a way you are contradicting pmsiar.

---

### Post by MicahCarrick on 2007-09-29
A lot of the RoR and Ruby developers I know use Text Mate on OSX. In Linux, they often (including myself) use Gedit. Gedit is more powerful that one would notice at first glance. Using the plug-ins you can setup gedit to perform the way you want. Throw in the terminal plugin, file browser plugin with an SSH connection to your server, and a few other plug-ins and you're in business.

Check out [Textmate-like Gedit in few steps]("http://grigio.org/textmate_gedit_few_steps") for instructions on setting up gedit to work like Textmate.

---

### Post by asimon on 2007-10-19
> **pmasiar said:**
> they cannot go around the fact that type information is known only at runtime. So you cannot have "intelliSense"-style method suggestion after you typed variablename-dot. Because you need to know type (class) to suggest methods, and I don't see any way around it. Do you?
Of course you can have intelliSense for dynamically typed languages. All IDEs worth their salt have that. Try for example NetBeans for Ruby/Rails [(See Tor's blog for screenshots)]("http://blogs.sun.com/tor/category/Ruby").

It's right that you have the full type information only at run time, but you do something which is called type inference which gives usually pretty good results. Of course Intellisense for statically typed languages will always be better (i.e. exact) then for dynamically typed langages, but the results are still very good and help to increase productivity.

Back to the original question, I prefer NetBeans for Ruby on Rails. As long as NB6.0 is not released I use the nightly builds from [http://wiki.netbeans.org/wiki/view/RubyInstallation](http://wiki.netbeans.org/wiki/view/RubyInstallation)

---

### Post by pmasiar on 2007-10-19
Yes, obviously, you can guess some. What you cannot do in IDE for dynamics is intellisense for function's parameters. Which is of course most of the code of a big project, right ?

---

### Post by Modred on 2007-10-19
I do my Rails work in Vim with the [rails plugin](http://www.vim.org/scripts/script.php?script_id=1567).  Without the plugin, the directory of a Rails app would be almost impossible to navigate efficiently; however, the plugin simplifies it to something like "Rmodel <model name>" to open a model, with similar functions for every other type of file you might have in a rails project.  It also provides nice commands to interface with rake and the files in script, among other things.

Couple it with Vim 7's omni-completion, and you more or less have an "IDE".

---

### Post by asimon on 2007-10-19
> **pmasiar said:**
> Yes, obviously, you can guess some.
Well, given the strong mathematical foundation of type theory, I would call it compute, not guess. ;-)

Also as it was shown, it's not only 'some' things, but fairly complete.

> **pmasiar said:**
> 
 What you cannot do in IDE for dynamics is intellisense for function's parameters. Which is of course most of the code of a big project, right ?
Yes, you can do intellisense for function paramerters too, it's a harder problem then doing it for statically typed languages, but possible, and good IDEs - of course - offer it.

I suppose, you didn't look at the screenshots I posted earlier, IIRC, there were some examples of parameter completions.

Netbeans, [SapphireSteel]("http://www.sapphiresteel.com/Evaluating-Ruby-IntelliSense"), 3rdRails, and to a lesser extend Radrails are all examples of IDEs doing the things you say are impossible.  :-)

---

### Post by loell on 2007-10-19
yup, dynamic IDE can do intellisense even in parameters too.

---

### Post by 1Michael1 on 2011-08-08
The last post was somewhat 4 years ago, I bet there's a lot more and better Ruby on Rails IDE's right now. Could we start naming a few that's good? I'm looking for one myself.

---

### Post by trivialpackets on 2011-08-08
> **1Michael1 said:**
> The last post was somewhat 4 years ago, I bet there's a lot more and better Ruby on Rails IDE's right now. Could we start naming a few that's good? I'm looking for one myself.

In ubuntu, I've found that you don't have Textmate which I've never tried, but heard it's quite popular, so the best options for editors that I have found are gedit and vim (when configured for rails development (see [here]("http://www.rubypluspl.us/2011/08/pursuit-of-rails-text-editor-on-linux.html") and [here]("http://www.rubypluspl.us/2011/08/vim-resources.html")).

With that said, I have tried a few different IDE's and I have been using RubyMine.  It's not free, however it works the best for me of all of the IDE's that I have tried.  There are some things though that I've never really gotten into.  I still do all rails generating, whether models, controllers, or migrations from the command line.  Basically all rails commands that I call are done from the command line, I don't use the IDE for that.  Also, I don't manage my git commits from the IDE, I do those as well from the command line.  

Basically I use the IDE like an editor, as I like the intellisense.  I would love to have a light-weight editor that was easy to use, offered intellisense and also the file view that I use.  Let me know if you find anything!  Feel free to check the links, they describe setting up the two editors, as those may be more than enough for you, depending on your requirements!

---

