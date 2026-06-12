---
title: "My search for an IDE"
date: 2009-05-31
forum: Programming Talk
---

### Post by Caliga on 2009-05-31
Im relitively new to Linux, have been using it for around about 6 months now on and off switching between Ubuntu and Windows (Currently running a dual boot between Jaunty/Se7en)

Ive programmed in Visual Basic for around 2 years now, and know the language pretty well - this has lead to some problems though. The basic language compared to that of C is messy and teaches you some very bad principles (for example I now swear out loud when using C++ and forget about case sensitivity). Visual studio itself has ment i've learned how to program, but only with a full set of tools. The IDE provides everything I need, with all the features I need.

What i'd like to know, if you chaps would be so kind as to help me out, is a decent suppliment for Visual Studio. I need an IDE that provides me with the following features Listed in order of importance):

1 - GUI creation: Drag and drop style interface, with easy reference to the objects that have been placed e.g txtBox1, Form1 etc.

2 - inbuilt compiler.

3 - Easy to understand debugging tools

4 - Code completion, like intellisense.

I'm not too bothered about the language, as learning a new one is always pretty fun, but I would like it to be similar to either the basic languages, or the C varients. I want to make programs for linux so I can join the community and maybe contribute something, even if its just small. If I can find an IDE that gives me everything I need in one place like visual studio did, ill be sorted :]

Thank you for any help you can give me in advance. Peace x

---

### Post by Habbit on 2009-05-31
The IDE you choose depends on the language you plan to use:
[LIST]
[*]C#, Visual Basic, other .NET languages: MonoDevelop. If you want the most complete support, use C# since VB only has only embrionary code completion support.
[*]Java: NetBeans, while it can be a bit slow, has served me well for long.
[*]Python: it depends... some people like IDLE, but I heard that the upcoming version of Netbeans has Python support too
[/LIST]

---

### Post by baizon on 2009-05-31
I'm using [Eclipse]("http://www.eclipse.org") for Java. In my opinion it feels more user friendly and more "professional" :)

---

### Post by SuperMike on 2009-05-31
I use ordinary Gedit that comes with Ubuntu, but I install this at command line:

# do this one only if you have like KDE and don't have gedit installed
$ sudo apt-get install gedit

# and now do this to install the plugins because normally these don't come by default
$ sudo apt-get install gedit-plugins



Then, go into Gedit and choose these plugins:

- Code Comment
- Document Statistics
- External Tools
- File Browser Pane (especially this one!)
- Indent Lines
- Modelines
- Session Saver
- Sort
- Spell Checker

And set tab stops to 4 and don't check "insert spaces instead of tabs". Also check (select) "Enable automatic indentation) and uncheck "Authosave files" and uncheck "create a backup copy". And then uncheck "enable text wrapping", check "display line numbers", check "highlight current line", check "display right margin" and usually I set that for 100 these days, and check "highlight matching bracket". 

On Fonts and Colors, after a lot of programming strain on my eyes for so long, I found relief with "Oblivion" theme, oddly enough.

Last, I go into the view menu of the editor and turn off some toolbars I don't normally use and make other adjustments with drag and drop and so on.

Oh, and I forgot -- I usually make an icon for this and fire it up with gksudo so that I can edit my HTML files in my /var/www directory.

However, note that you won't get a GUI editor for editing GUI things like buttons and so on with this thing. Sorry.

---

### Post by simeon87 on 2009-05-31
> **Caliga said:**
> 1 - GUI creation: Drag and drop style interface, with easy reference to the objects that have been placed e.g txtBox1, Form1 etc.

Glade can do this for Gtk: [http://glade.gnome.org/](http://glade.gnome.org/).

---

### Post by Caliga on 2009-05-31
I shall give these things a try, but is there nothing that has all the features of visual studio in it already? Without having to get other components to use with it? What im really looking for is an all in one solution.

Worst comes to worst I could always just make applications using visual studio, and then use wine to run them on here - but that kinda takes the fun out of linux.

---

### Post by simeon87 on 2009-05-31
> **Caliga said:**
> I shall give these things a try, but is there nothing that has all the features of visual studio in it already? Without having to get other components to use with it? What im really looking for is an all in one solution.

Why would you need an all-in-one solution? It is part of the Unix philosophy to do one thing and to do it well: [http://en.wikipedia.org/wiki/Unix_philosophy](http://en.wikipedia.org/wiki/Unix_philosophy). Therefore, it's better to have separate components so you can replace each of them with a better one if needed. It also prevents programs from growing too large and becoming bloated.

---

### Post by Habbit on 2009-05-31
Well, both Eclipse and NetBeans sport the kind of full support you search for Java programs: code completion, GUI builders, etc. MonoDevelop also does for C#, although I can't find its Windows Forms designer it has an alternative Gtk# designer. Besides, you can use Visual Studio and run apps in Linux without Wine - just use a .net language like VB.net or C#, as Mono support comes with Ubuntu.

---

### Post by tyfius on 2009-05-31
I use different tools for different tasks.

For quick editing I use Vim with a bunch of extra plugins (code completion, snippets, nerdtree, ...) but when I'm working on a bigger project I like to use a full blown IDE, or at least something with more specialized features than Vim.

[LIST]
[*]For C/C++ I use Code::Blocks. I switched to it because I felt that Anjuta became less stable and less organized. Code::Blocks integrates all the required features (debugger, code completion, project management, ...).
[*]For PHP projects I originally used Vim but switched to Eclipse PDT because it had more features. Recently I switched to NetBeans 6.5 (and now 6.7M2) because it uses less memory than Eclipse and I can find myself more in the environment.
[*]For C# projects I MonoDevelop. Quick and easy. I feel that it's not yet mature when it comes to C/C++ so I stick to Code::Blocks for that. MonoDevelop also contains a GUI designer like Visual Studio does, otherwise you can use Glade which generates XML based layouts. You can compare it best with WPF.
[/LIST]

I have tried Gedit with a bunch of plugins but I just like to use the right tool for the right job which, at the end, saves me time.

Also note that, unlike what seems to have been described in the post above mine, Visual Studio does not run on Linux with Wine. For it you'll need to use a virtual machine which runs a full Windows version. Unfortunately there is not really an IDE on Linux (or Mac) which fully matches up to Visual Studio so we need to combine the things available to us. :)

---

### Post by gishaust on 2009-05-31
I use netbeans for the following reasons. It will program in
Java 
PHP
JavaFx
css
xHtml
Javascript
and many other languges....


It can look danting at the start.It took me about a week to work most things out. It has a great formating tool and hundreds of options.

To install it all you have to do is  sudo aptitude install netbeans (or something like that. Then update the netbeans ide itself.

The only let down is on ubuntu it is usually two versions behind in the packages. But you can build it from scratch if you want to.

Great Tool and have never had any issues with it

---

### Post by mdurham on 2009-05-31
For C++ use QtCreator. It has all the things that you require. Code::Blocks isn't too bad, but GUI creation was very strange and it didn't have Cut & Paste using the mouse (can you believe!), so I was very glad to find QtCreator.
Good luck, whatever you use.
Mike

---

### Post by wiseguyin on 2009-06-05
[FONT="Comic Sans MS"]This resonates with my own search ...

I have been trying to contribute to some open source projects (specifically) GIMP, but find that there is no way to even understand how to debug it. Virtually all my experience in programming comes from windows (i have done a lot of COM/C++/C#/vb.net/IVR coding). So it is unsettling to find that the projects in linux that you wish to contribute to have no
counterpart to the IDE based workflow !


PS: And I hate all that emacs fanboyism ...[/FONT]

---

