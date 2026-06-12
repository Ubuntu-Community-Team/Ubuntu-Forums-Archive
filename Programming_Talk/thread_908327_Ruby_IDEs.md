---
title: "Ruby IDEs"
date: 2008-09-02
forum: Programming Talk
---

### Post by Paul Miller on 2008-09-02
Other than Eclipse/Emacs/Vim (which I want to avoid for my own personal reasons), what IDEs do folks recommend for Ruby programming on Ubuntu?  My personal requirements include:

[LIST]
[*]It's not Eclipse/Emacs/Vim (personal prejudice)
[*]Syntax highlighting
[*]Code reformatting
[/LIST]

Does anyone have any suggestions?

Thanks!

---

### Post by jimi_hendrix on 2008-09-02
geany supports ruby...i dont know how good it is thought since i dont know ruby

---

### Post by AxiomShell on 2008-09-02
Not Open source (or even free as in beer) but you can try IntelliJ IDEA.

You get excellent Ruby/JRuby support (refactoring, testing, debugging) and also the best (by far) Groovy support and (IMHO) the best Java support.

---

### Post by Balazs_noob on 2008-09-02
if you don't mind that it is heavy then Netbeans
( never used it for ruby thought but it supports it )

---

### Post by rogeriopvl on 2008-09-02
Geany or... gedit.

---

### Post by Ruhe on 2008-09-02
Don't know about code formating, but scite is good lighweight editor.

*<% start_hollywar %>*But comparing with vim or emacs, scite is silly.*<% end_hollywar %>*

---

### Post by loell on 2008-09-02
openkomodo / komodo edit.

---

### Post by rye_ on 2008-09-02
I use gedit (geany also good)
make sure you add the following plugins;

-sidepane folder browser
-external tools (then add a script to run the file)
-snippets

from website
-snapopen plugin

The tab completion of code snippets in both gedit and geany makes coding very pleasant.

---

### Post by Sinkingships7 on 2008-09-02
+1 for Geany. AMAZING little application.

---

### Post by mssever on 2008-09-02
> **Paul Miller said:**
> 
[LIST]
[*]Code reformatting
[/LIST]
I'm not exactly sure what you mean by code reformatting, but when I write Ruby, I use vim and gedit with plugins. Neither does a whole lot of code reformatting. I've heard that some people like Netbeans, but I don't know much about it. I tried it once, and it seemed to me like overkill.

---

### Post by jespdj on 2008-09-03
> **Balazs_noob said:**
> if you don't mind that it is heavy then Netbeans
( never used it for ruby thought but it supports it )
NetBeans has very good support for Ruby.

---

### Post by billstei on 2008-12-19
Decided to try Netbeans as a Ruby IDE and there are a few issues with version 6.1 as provided in Intrepid (and Jaunty thus far) that make it not work out-of-the-box.  With packages: ruby, ruby1.8-dev, rubygems, netbeans installed (via Synaptic) it is necessary to make sure the following two gems are not greater than the following revs:

ruby-debug-base (0.10.1)
ruby-debug-ide (0.1.10)

as documented here:

[http://wiki.netbeans.org/RubyDebugging61](http://wiki.netbeans.org/RubyDebugging61)

having downloaded these two gems directly from here:

[http://rubyforge.org/frs/?group_id=3085](http://rubyforge.org/frs/?group_id=3085)

then the commands to install these gems can be simplified as:

sudo gem install ruby-debug-base-0.10.1-java.gem
sudo gem install --ignore-dependencies ruby-debug-ide-0.1.10.gem

You can check which gems you have with:

gem list

Once in Netbeans for the first time, in menu Tools->Plugins->Available Plugins, if you only install Ruby and Rails, it will result in an (constantly nagging) error in the setup of the built-in JRuby, which shows in red in the Ruby Platforms list, and stubbornly refuses to be Removed, even given that a standard Ruby intrepreter is present, and even if the error is resolved.  The solution is to check JRuby and Rails Distribution plugin (again under Availiable Plugins) and install that (first).  Assuming then, that JRuby is not the interpreter desired, remember to (un)choose it when making a Ruby project, or after-the-fact in File->[MyProject]Properties->Run->Ruby Platform.

It is also worth noting that the gem path for the standard gem/ruby in Ubuntu is: /var/lib/gems/1.8 which Netbeans seems to find without any trouble.

Bill

---

