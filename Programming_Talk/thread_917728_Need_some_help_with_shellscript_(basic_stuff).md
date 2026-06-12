---
title: "Need some help with shellscript (basic stuff)"
date: 2008-09-12
forum: Programming Talk
---

### Post by pedrotuga on 2008-09-12
I am trying to automate the process of creating timestamped tarballs.

I wrote this tinny script and it does the job, except that it doesn't clean the forward slash in the end of the folder name if included.

```
#!/bin/bash
date "+%Y.%m.%d-%H.%m" | xargs -I {} tar -cvvzf  {}$1.tar.gz  $1
```

Now that is working fine. But I got a few things I would like to know.

First, before getting the hint of using xargs, I was comming up with something like this:

[PHP]#!/bin/bash

datestring=date "+%Y.%m.%d-%H.%M_"
foldername=$1
tarballname="${datestring}${foldername}.tar.gz"

tar -cvvzf "$tarballname" $1
echo $tarballname[/PHP]

that doesn't work. The problem is that the first like of code is not correct. The question is obvious: **How do I get a command output into a variable?**

The other question is: I**s there anyway to make this script acessible from everywhere without placing it outside my user home folder?**

And finally:
How can I drop the last char of a string in case it's a forward slash?

---

### Post by ghostdog74 on 2008-09-12
> **pedrotuga said:**
> 
[PHP]#!/bin/bash

datestring=date "+%Y.%m.%d-%H.%M_"
foldername=$1
tarballname="${datestring}${foldername}.tar.gz"

tar -cvvzf "$tarballname" $1
echo $tarballname[/PHP]
```

datestring=$(date "+%Y.%m.%d-%H.%M_")
foldername=$1
tarballname="${datestring}${foldername}.tar.gz"
tar -cvvzf "$tarballname" $1
echo $tarballname  

```

> 
**How do I get a command output into a variable?**

use backticks: var=`command` or var=$(command)

[quote]
The other question is: I**s there anyway to make this script acessible from everywhere without placing it outside my user home folder?**

edit your PATH env variable

> 
And finally:
How can I drop the last char of a string in case it's a forward slash?
```

# var="/home/"
# echo $var | sed -e 's/\/$//'
/home


```

---

### Post by pedrotuga on 2008-09-12
Thank you. Those were clear answers to all the questions :)

Just one more little question: when using backticks, do the cariables get expanded with their content?

---

### Post by ghostdog74 on 2008-09-12
> **pedrotuga said:**
> Just one more little question: when using backticks, do the cariables get expanded with their content?
you can always try it out yourself on the shell prompt. create a variable, give the variable to the command and then echo the variable to see if its expanded.
eg
```

f=file #file name
var=`date -r $f`
echo $var

```

---

### Post by pedrotuga on 2008-09-13
Ok this is a lot of fun.
I'll take the chance to learn some more stuff.

Let's sa I place my script in /usr/bin which I believe is the apropriate location, now I would like to create a manage. Is there anyway to embed a manpage into the script file itself?

So far the only way of creating manpages I found uses a tool called groff. But i noticed some perl applications have docs in the end of the source file, in a simpler format. I don't know... I guess those can only be fetched by perldoc.

For example, zim desktop wiki has this

```
__END__

=head1 NAME

zim - A desktop wiki and outliner

=head1 SYNOPSIS

B<zim> [I<OPTIONS>] [I<NOTEBOOK> [I<PAGE>]]

=head1 DESCRIPTION

B<Zim> is a desktop wiki writtin in perl using Gtk2.

Try to execute C<zim --doc> to view the user manual.

=head1 OPTIONS

=over 4

=item B<--doc>

Open the zim documentation.

=item B<--export> I<OPTIONS>

Export pages to another format. OPTIONS should at least
contain 'dir' and 'format', and optionally 'template',
and 'media'.

Example:

	zim --export dir=./html,format=html ./Wiki

This will export all pages in the notebook dir "./Wiki"
to a dir "./html" using the html format.

=item B<-p>, B<--profile> I<NAME>

Open using a certain profile. For example use C<-p reader>
to open a notebook read-only.

=item B<--type> I<NAME>

Give the type for a new notebook.

=item B<--pidfile> I<FILE>

Write the process id of to I<FILE>.

=item B<--geometry> I<W>xI<H>[+I<X>+I<Y>]

Set the size of the main window to I<W>xI<H> pixels
and position the window at I<X>,I<Y>.

=item B<--iconify>

Start zim iconified. If the TrayIcon plugin is enabled
this option will start zim in the system tray.

=item B<--quiet>

Do not print any information to the terminal.

=item B<-V>, B<--verbose>

Print more verbose information to the terminal.

=item B<-D>, B<--debug>

Print developer information to the terminal.

=item B<-v>, B<--version>

Print version and copyright information and quit.

=back

=head1 AUTHOR

Jaap Karssenberg E<lt>pardus@cpan.orgE<gt>

Copyright (c) 2005, 2007 Jaap G Karssenberg. All rights
reserved. This program is free software; you can redistribute it and/or
modify it under the same terms as Perl.

This program is distributed in the hope that it will be useful, but
WITHOUT ANY WARRANTY; without even the implied warranty of MER-
CHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See either the GNU
General Public License or the Artistic License for more details.

=head1 SEE ALSO

L<Zim>(3)

=cut
```

---

