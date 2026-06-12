---
title: "Ruby &amp; Gedit (In context) Syntax Highlighting"
date: 2008-06-07
forum: Programming Talk
---

### Post by rye_ on 2008-06-07
Hi,

I'm quite partial to gedit as my editor for ruby scripting tasks, which fails only in one respect; its syntax highlighting.  I've posted a script I wrote which examples the problem.

```

#!/usr/bin/ruby -w

#---------------
#new_ruby.rb
#	A script to enable the naming, saving of a .rb file, together with 
#making executable and adding the shebang line in a single, quick action
#NOTE: use by adding an alias to .bashrc
#

##handle file input, convert file input to the complete file path
raise "no file path given, exiting..." unless defined? ARGV[0]
file = (ARGV[0] if ARGV[0] =~ /\//) || Dir.pwd + "/" + ARGV[0];

#Ensure that the file ends .rb
raise "file type must be named with the suffix .rb" unless file =~ /(\/)(\w+\.rb)/
##Ensure the file does not exist
Dir.chdir($`[COLOR="Red"])
Dir["*"].each {|x| raise "file already exits, exiting..." if x == $2}

##file operations
File.open(file, 'w') {|f| f.puts "#!/usr/bin/ruby -w"}
File.chmod(0755, file)
%x{gedit #{file}}
exit #get rid of the hanging terminal[/COLOR]

```

This code is my update of an earlier script I wrote which automates the creation of a ruby file as a time saver.  When viewed in gedit however, gedit fails to recognise the global variables $' ad $` as single units instead highlighting everything after the accent as a string that never ends.  i.e. it thinks all instances of ' and ` are string delimiters.

This is quite irritating and can make very things difficult to read.

My question is, has anyone come up with a fairly straightforward way of solving this? Can I avoid having to write my own syntax logic for gedit.

Thanks in advance,

Ryan

---

### Post by rye_ on 2008-06-07
well, perhaps I'll have to eventually learn xml to solve this issue properly.
 
Until then I'll have to continue adding the comment #` and #' after the relevant global variables to fix the highlighting.



Ryan


EDIT:BUG REPORT SUBMITTED, ISSUE RESOLVED

---

### Post by pmuflon on 2008-07-02
Hi, I've got one question. In which version the bug is fixed? I have gedit 2.22.3 from hardy updates repository, and it has this bug... Did you use some version from repository or build this program from sources?


Peter

---

