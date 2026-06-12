---
title: "A good Ruby on Rails IDE."
date: 2008-04-30
forum: Programming Talk
---

### Post by japtar10101 on 2008-04-30
In preparation for a project next year, I'm looking for a really good IDE for Ruby on Rails.  I wanted to ask, what IDEs are really good for Rails?

In my experience, I prefered Aptana's RadRails, but for some reason, my laptop's Ubuntu partition has a hard time trying to download both Aptana and Rad Rails for Eclipse (I tried downloading RadRails through Aptana...didn't work).  I somewhat like the jEdit's split screen, but the Hardy Heron jEdit package doesn't run on this laptop either.  I have yet to try netbeans...but I will soon.

I don't plan on using emacs or scite (or Gedit) for this.  It's too much of a hassle to look through the directories with them.

---

### Post by gjj391 on 2008-04-30
aptana (radrails plugin).... netbeans (rails plugin)....

FIX: sorry didnt read your whole post about aptana... try netbeans.

---

### Post by tw3k on 2008-04-30
anjuta is a pleasant editor with a built-in file browser.

---

### Post by rye_ on 2008-05-01
Of course, textmate is the editor of choice for the mac, which seems to be a common rails development platform in the rails community.

Gnome has gedit, which can possess all the same features via plugins (see my screenshot in the attachment).  That's using the bash shell, snap open, file browser, class browser, and code snippets plugins.  Using  plugins (some of which are in the repos) makes gedit excellent for programming.

Additional plugins can be found on the gedit website, and should be extracted to ~/.gnome2/gedit/plugins


I hope that helps you (It's certainly the tool I use for Rails/Ruby).

Ryan

---

### Post by Hyperkill on 2008-05-01
> **rye_ said:**
> Of course, textmate is the editor of choice for the mac, which seems to be a common rails development platform in the rails community.

Gnome has gedit, which can possess all the same features via plugins (see my screenshot in the attachment).  That's using the bash shell, snap open, file browser, class browser, and code snippets plugins.  Using  plugins (some of which are in the repos) makes gedit excellent for programming.

Additional plugins can be found on the gedit website, and should be extracted to ~/.gnome2/gedit/plugins


I hope that helps you (It's certainly the tool I use for Rails/Ruby).

Ryan

Very nice setup you've got there, Ryan.  Thanks for sharing it.

---

### Post by japtar10101 on 2008-05-01
> **rye_ said:**
> Of course, textmate is the editor of choice for the mac, which seems to be a common rails development platform in the rails community.

Gnome has gedit, which can possess all the same features via plugins (see my screenshot in the attachment).  That's using the bash shell, snap open, file browser, class browser, and code snippets plugins.  Using  plugins (some of which are in the repos) makes gedit excellent for programming.

Additional plugins can be found on the gedit website, and should be extracted to ~/.gnome2/gedit/plugins


I hope that helps you (It's certainly the tool I use for Rails/Ruby).

Ryan
I'll try that, thanks.

---

### Post by rye_ on 2008-05-08
I ought to have also mentioned the (very useful) 'external tools' plugin which is part of the gedit plugins package in the repos.

EDIT see [http://ubuntuforums.org/showthread.php?p=4927397#post4927397]("http://ubuntuforums.org/showthread.php?p=4927397#post4927397")

Ryan

---

### Post by WitchCraft on 2008-05-08
> **japtar10101 said:**
> In preparation for a project next year, I'm looking for a really good IDE for Ruby on Rails.  I wanted to ask, what IDEs are really good for Rails?

In my experience, I prefered Aptana's RadRails, but for some reason, my laptop's Ubuntu partition has a hard time trying to download both Aptana and Rad Rails for Eclipse (I tried downloading RadRails through Aptana...didn't work).  I somewhat like the jEdit's split screen, but the Hardy Heron jEdit package doesn't run on this laptop either.  I have yet to try netbeans...but I will soon.

I don't plan on using emacs or scite (or Gedit) for this.  It's too much of a hassle to look through the directories with them.


I'd try Python instead of Ruby. It's much more powerful.

---

### Post by japtar10101 on 2008-05-08
> **WitchCraft said:**
> I'd try Python instead of Ruby. It's much more powerful.

I prefer Ruby's Object Orientation syntax than Python's, actually.  Also, I'm looking towards web developing, and while Python can create many websites with CGI, PHP and Ruby on Rails are more specialized to the task.

I am trying to learn Python, though....I never found the time.

---

### Post by rye_ on 2008-05-08
> **WitchCraft said:**
> I'd try Python instead of Ruby. It's much more powerful.

In what way WitchCraft?

---

### Post by brink on 2008-05-08
Vim with [rails.vim]("http://rails.vim.tpope.net/") is amazing.

Caveat: with hardy there's a memory bug that exhibits itself via segfaults when you tab complete, so I can't recommend it for Hardy users at the moment... maybe when Ubuntu gets Vim patch 259 (it's currently at 138).

---

### Post by rye_ on 2008-05-08
I must say I've always (we'll, the last year or so) quite fancied the idea of learning a more shortcut reliant editor. Do you find it more efficient?

Also, would you mind posting you vim configuration files.

Thanks

---

### Post by brink on 2008-05-09
It feels more efficient to me. At least, for the rails dev I do there's less hunting around trying to find files.

Example: I'm editing user.rb and realize I need to edit the user controller. I type the following:
<ESC>
:Rcont
<ENTER>

Or say I'm editing the Author model file which has_many :books. Suddenly I need to check something in the books file. I put the cursor on the line of text that says "has_many :books", type type the letters 'gf' and suddenly I'm editing books.rb, or authorbooks.rb or whatever i happen to have called the file containint the Books model.

That's just with rails.vim. There are ALL sorts of other things you can do like search and replace with regexes, vertical selection, etc. 

The only hurdle to using it is getting into the idea of the editor having a state ("Normal" and "Edit") and the idea that the editor needs a current working directory.

Lastly, I'll try to get vim config files, but I don't have access to my work machine right now.

---

### Post by brink on 2008-05-09
Attempting to attach my .vimrc, but this interface is screwy.

Also, the plugins I use are project, rails.vim, mini buffer explorer, and netrw (for editing in GVim via gvfs).

---

### Post by rye_ on 2008-05-09
thanks very much, I really appreciate that.

Ryan

---

### Post by rye_ on 2008-05-10
The last post I'll make on the subject, but.....

finding myself using needing gedit for a bit of python as well as ruby, my revised 'external tools plugin' run script. May be useful for others.
just assign a keyboard shortcut in order to use the script, to interpret directly perl, python or ruby files.

```

#!/usr/bin/ruby

#(0...ENV.length).each {|x| puts "#{ENV.keys[x]} : #{ENV.values[x]}"} #useful environment variables

#check that the input file is appropriate
raise "not a ruby, python or perl file"  unless  ENV['GEDIT_CURRENT_DOCUMENT_NAME'] =~ /\.(rb|p(y|l))/

#use the appropriate interpreter
interpreter_hash = {'.rb' => 'ruby', '.py' => 'python', '.pl' => 'perl'}
interpreter = nil
interpreter_hash.keys.each {|x|  interpreter = interpreter_hash[x]; break if x == $& }

puts  `#{interpreter} #{ENV['GEDIT_CURRENT_DOCUMENT_PATH']}`

```

Ryan

---

### Post by simontol on 2008-06-04
You should try Geany
[http://geany.uvena.de/](http://geany.uvena.de/)

0.13 is in repositories.

0.14 here: [http://getdeb.net/search.php?keywords=geany](http://getdeb.net/search.php?keywords=geany)

---

### Post by xlinuks on 2008-06-04
Perhaps the most complete support for Ruby has NetBeans, have a look:
[http://wiki.netbeans.org/Ruby](http://wiki.netbeans.org/Ruby)

---

### Post by ocdude on 2008-06-10
> **rye_ said:**
> 

Additional plugins can be found on the gedit website, and should be extracted to ~/.gnome2/gedit/plugins


I hope that helps you (It's certainly the tool I use for Rails/Ruby).

Ryan

Are those the same that are found in the package gedit-plugins? I'm at work, so I can't really check on my machine.

---

### Post by rye_ on 2008-06-10
Some are.
Though I think that at least the snapopen plugin is missing from synaptic.

---

