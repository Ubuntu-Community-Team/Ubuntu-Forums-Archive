---
title: "Can some one look at this Perl Script Please"
date: 2010-07-31
forum: Programming Talk
---

### Post by k33bz on 2010-07-31
First off it is not my script, I dont want to be told I am trying to take credit for it.

I got this script from a site here :[http://micksmix.wordpress.com/2009/11/20/getting-the-backtrack-menu-structure-and-tools-in-ubuntu/]("http://micksmix.wordpress.com/2009/11/20/getting-the-backtrack-menu-structure-and-tools-in-ubuntu/")

Me as well as others have had problems running it correctly. I personally get this error when I run it:
```
keebler@mobile:~/tools$ sudo perl updateBTmenu.pl
Argument "false" isn't numeric in smart match at updateBTmenu.pl line 66.
Argument "false" isn't numeric in smart match at updateBTmenu.pl line 66.


All menu entries have been updated

```

Although my menu does not get updated at all. Here is the script:

```
001	#!/usr/bin/perl
002	#
003	##
004	# Written by Mick Grove
005	# http://micksmix.wordpress.com
006	#
007	#  [v0.1]       11/20/2009
008	##
009	#
010	# BSD Licensed
011	#
012	#       Redistribution and use in source and binary forms, with or without
013	#       modification, are permitted provided that the following conditions are
014	#       met:
015	#
016	#       * Redistributions of source code must retain the above copyright
017	#         notice, this list of conditions and the following disclaimer.
018	#       * Redistributions in binary form must reproduce the above
019	#         copyright notice, this list of conditions and the following disclaimer
020	#         in the documentation and/or other materials provided with the
021	#         distribution.
022	#       * Neither the name of the  nor the names of its
023	#         contributors may be used to endorse or promote products derived from
024	#         this software without specific prior written permission.
025	#
026	#       THIS SOFTWARE IS PROVIDED BY THE COPYRIGHT HOLDERS AND CONTRIBUTORS
027	#       "AS IS" AND ANY EXPRESS OR IMPLIED WARRANTIES, INCLUDING, BUT NOT
028	#       LIMITED TO, THE IMPLIED WARRANTIES OF MERCHANTABILITY AND FITNESS FOR
029	#       A PARTICULAR PURPOSE ARE DISCLAIMED. IN NO EVENT SHALL THE COPYRIGHT
030	#       OWNER OR CONTRIBUTORS BE LIABLE FOR ANY DIRECT, INDIRECT, INCIDENTAL,
031	#       SPECIAL, EXEMPLARY, OR CONSEQUENTIAL DAMAGES (INCLUDING, BUT NOT
032	#       LIMITED TO, PROCUREMENT OF SUBSTITUTE GOODS OR SERVICES; LOSS OF USE,
033	#       DATA, OR PROFITS; OR BUSINESS INTERRUPTION) HOWEVER CAUSED AND ON ANY
034	#       THEORY OF LIABILITY, WHETHER IN CONTRACT, STRICT LIABILITY, OR TORT
035	#       (INCLUDING NEGLIGENCE OR OTHERWISE) ARISING IN ANY WAY OUT OF THE USE
036	#       OF THIS SOFTWARE, EVEN IF ADVISED OF THE POSSIBILITY OF SUCH DAMAGE.
037	#
038	#
039	use strict;
040	use warnings;
041	use Tie::File;
042	 
043	my $dir     = "/usr/local/share/applications";
044	my $section = "Desktop Entry";
045	my $in_section;
046	my @files;
047	 
048	opendir(BIN, $dir) or die "Can't open $dir: $!";
049	while (defined(my $file = readdir BIN))
050	{
051	    next if $file =~ /^\.\.?$/;    # skip . and ..
052	    if ($file =~ m/.*\.desktop$/i)
053	    {
054	        push(@files, $file);
055	    }
056	}
057	closedir(BIN);
058	 
059	foreach my $curfile (@files)
060	{
061	    open(FH, "<", "$dir/$curfile") or die "$!";
062	    chomp(my @fileparts = <FH>);
063	    close(FH);
064	 
065	    my $termval = TerminalStatus(\@fileparts);
066	    next if $termval == 0;    # skip if this is not a terminal application
067	 
068	    #lets see if this is actually a BT program
069	    my $btprogram = IsBTProgram(\@fileparts);
070	    next if $btprogram == 0;    # skip if this is not a BT application
071	 
072	    my $ExecKey     = "Exec";
073	    my $TerminalKey = "Terminal";
074	    my @tiedfile;
075	 
076	    #open this file for editing
077	    tie @tiedfile, 'Tie::File', "$dir/$curfile" or die "$!";
078	 
079	    #read file line by line here
080	    # updating "Exec" line
081	    foreach my $fline (@tiedfile)
082	    {
083	        next if $fline =~ /^#/;       # skip comments
084	        next if $fline =~ /^\s*$/;    # skip empty lines
085	 
086	        if ($fline =~ /^\[$section\]$/)
087	        {
088	            $in_section = 1;
089	            next;
090	        }
091	 
092	        if ($fline =~ /^\[/)
093	        {
094	            $in_section = 0;
095	            next;
096	        }
097	 
098	        my $oldline;
099	        my $updatedline;
100	        if ($in_section and $fline =~ /^$ExecKey\s*=\s*(.*)$/)
101	        {
102	 
103	            # this means we have the "Exec key"
104	            $oldline = $1;
105	            next if $oldline =~ m/^.*xterm -e.*;bash.*$/i;    #skip
106	            $oldline =~ s/"/\\"/img;
107	            $updatedline = "Exec=xterm -e \"$oldline;bash\"";
108	            $fline       = $updatedline;
109	 
110	            print "New exec: " . $fline . "\n";
111	            next;
112	        }
113	        elsif ($in_section and $fline =~ /^$TerminalKey\s*=\s*(.*)$/)
114	        {
115	 
116	            # this means we have the "Terminal key"
117	            # we will set it to "0" to turn it off --- we are launching
118	            #   xterm ourselves, if we set to 1, we'll get an extra
119	            #   terminal opened
120	            #
121	            $oldline     = $1;
122	            $updatedline = "Terminal=0";
123	            $fline       = $updatedline;
124	            next;
125	        }
126	 
127	    }
128	    untie @tiedfile;
129	}
130	 
131	print "\n\nAll menu entries have been updated\n";
132	 
133	###
134	### Subroutines ###
135	###
136	sub TerminalStatus
137	{
138	    my @lines       = @{$_[0]};
139	    my $TerminalKey = "Terminal";
140	    my $ExecKey     = "Exec";
141	    my $termkeyval  = 0;            #default = 0 FALSE, 1= TRUE
142	    my $i           = 0;
143	    my $execkeyval = 0;  #default = 0 = this exec line probably wasn't set by us
144	 
145	    foreach my $fline (@lines)
146	    {
147	        next if $fline =~ /^#/;       # skip comments
148	        next if $fline =~ /^\s*$/;    # skip empty lines
149	 
150	        if ($fline =~ /^\[$section\]$/)
151	        {
152	            $in_section = 1;
153	            next;
154	        }
155	 
156	        if ($fline =~ /^\[/)
157	        {
158	            $in_section = 0;
159	            next;
160	        }
161	 
162	        if ($in_section and $fline =~ /^$TerminalKey\s*=\s*(.*)$/)
163	        {
164	 
165	            # this means we have the "terminal key"
166	            $termkeyval = $1;
167	            next;    #last;
168	        }
169	 
170	        if ($in_section and $fline =~ /^$ExecKey\s*=\s*(.*)$/)
171	        {
172	 
173	            # this means we have the "exec key"
174	            $execkeyval = $1;
175	            if ($execkeyval =~ m/^.*xterm -e.*;bash.*$/i)
176	            {
177	                $execkeyval = 1;    # this script likely set this value before
178	            }
179	            next;                   #last;
180	        }
181	    }
182	 
183	    if ($execkeyval eq 1)
184	    {
185	        # force this to true, because this can be updated by this script,
186	        #   b/c we appear to have modified this entry before.
187	        $termkeyval = 1;
188	    }
189	    return $termkeyval;
190	}
191	 
192	sub IsBTProgram
193	{
194	    my @lines    = @{$_[0]};
195	    my $key      = "Categories";
196	    my $isbtprog = 0;              #default = FALSE = 0
197	    my $i        = 0;
198	    foreach my $fline (@lines) {
199	        next if $fline =~ /^#/;       # skip comments
200	        next if $fline =~ /^\s*$/;    # skip empty lines
201	 
202	        if ($fline =~ /^\[$section\]$/) {
203	            $in_section = 1;
204	            next;
205	        }
206	 
207	        if ($fline =~ /^\[/) {
208	            $in_section = 0;
209	            next;
210	        }
211	        if ($in_section and $fline =~ /^$key\s*=\s*(.*)$/)
212	        {
213	 
214	            # this means we have the "terminal key"
215	            if ($1 =~ m/.*BT-.*/i)
216	            {
217	                $isbtprog = 1;
218	            }
219	            last;
220	        }
221	    }
222	    return $isbtprog;
223	}
```

I have try editing line 66 from looking at other sites, making it various combinations but to no avail. These are the ones I have tried:

```

1.  next if $termval == "";    # skip if this is not a terminal application

2.  next if $termval == " ";    # skip if this is not a terminal application

3.  next if $termval eq 0;    # skip if this is not a terminal application

4   next if $termval ~~ 0;    # skip if this is not a terminal application
```

I either get the same errors with usually another error added to it. Or I get no errors, but my menus dont do anything still. The one where I dont get any errors is when I used "eq"


Sorry so long :( Plz help

---

### Post by Some Penguin on 2010-07-31
If the TerminalStatus subroutine can return the scalar value "false", perhaps the most obvious thing is to replace the comparison with a check against... "false".

```

next if $termval eq 'false';

```

---

### Post by k33bz on 2010-07-31
> **Some Penguin said:**
> If the TerminalStatus subroutine can return the scalar value "false", perhaps the most obvious thing is to replace the comparison with a check against... "false".

```

next if $termval eq 'false';

```

thanks, :(

although it did not show any errors, making it look very successful, my menu has not changed :(. I can get the same results by omitting line 66 all together :(

You have any other ideas? (Im not a programmer, dont know much about it at all, but I am trying to learn perl right now)

Just really wondering if there is something else wrong with the script besides line 66, maybe some other line that works with line 66. termval only shows up in lines 65 and 66.

---

### Post by gmargo on 2010-07-31
The bug is on line 166, where the TerminalStatus subroutine does not translate the "Terminal=..." value properly.

Change line 166 to:
```

            $termkeyval = lc($1 || "") eq "true" ? 1 : 0;

```

---

### Post by k33bz on 2010-07-31
> **gmargo said:**
> The bug is on line 166, where the TerminalStatus subroutine does not translate the "Terminal=..." value properly.

Change line 166 to:
```

            $termkeyval = lc($1 || "") eq "true" ? 1 : 0;

```

Ok, I changed line 166, no errors, yet no update on menu structure either. So I changed line 66 back to what it was originally:

line 66 first time ran:
```
next if $termval eq 'false';
```

original code I changed it back to
```
next if $termval == 0;    # skip if this is not a terminal application

```

and again no errors. So I guess that takes care of th bug the script had. However the script still dont do what it is suppose to do. :(

---

### Post by gmargo on 2010-07-31
> **k33bz said:**
> However the script still dont do what it is suppose to do. :(

What do you think the script is supposed to do?  It looks like it's editing .desktop files under /usr/local/share/applications/.  It won't cause new menu entries to show up.  The other steps in that blog entry are for modifying the menu - did you do all of that?

---

### Post by k33bz on 2010-07-31
> **gmargo said:**
> What do you think the script is supposed to do?  It looks like it's editing .desktop files under /usr/local/share/applications/.  It won't cause new menu entries to show up.  The other steps in that blog entry are for modifying the menu - did you do all of that?


yes the menus are there, can verify it by editing menus and seeing that they are there. And the apps are installed. The script was suppose to list those apps inside the backtrack menus (that are already been created). Yet none of them show up in my menu.

---

### Post by k33bz on 2010-07-31
*bump*

---

### Post by gmargo on 2010-07-31
I tried to follow the Backtrack installation procedure but am getting no response from the repository at [http://repo.offensive-security.com/dist/]("http://repo.offensive-security.com/").  Is there another repo to use?

---

### Post by k33bz on 2010-07-31
> **gmargo said:**
> I tried to follow the Backtrack installation procedure but am getting no response from the repository at [http://repo.offensive-security.com/dist/]("http://repo.offensive-security.com/").  Is there another repo to use?

this is the one that worked for me:

```
http://archive.offensive-security.com pwnsauce main microverse macroverse universe multiverse
```

> 

New Steps to add repository

1. HOW TO IMPORT ARCHIVE GPG KEY IN YOUR SYSTEM
Command : wget -q [http://archive.offensive-security.com/backtrack.gpg](http://archive.offensive-security.com/backtrack.gpg) -O- | sudo apt-key add -

2. HOW TO ADD THE MAIN REPOSITORY
Command : sudo echo &#8220;deb [http://archive.offensive-security.com](http://archive.offensive-security.com) pwnsauce main microverse macroverse restricted universe multiverse&#8221; > /etc/apt/sources.list

3. INSTALL THE REPOSITORY
You have to reload and select package you want to install through synaptic package manager

Wish you luck^^


there is a txt for all the backtrack tools that come pre-installed, however the one I had will break your system, at least it broke mine, had to do a fresh install. You will just have to go one by one to add the tools you want from synaptic. Caution again though is that some tools wont work, cant install they will go through a dependecy hell. 

Ones I remember that you  cant install are
grabber
wireless-regdb-git
wifizoo
wifitap
scapy
scapy2
python-scapy

---

### Post by k33bz on 2010-08-05
*bump*

---

