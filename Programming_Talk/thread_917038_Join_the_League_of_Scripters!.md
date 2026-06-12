---
title: "Join the League of Scripters!"
date: 2008-09-11
forum: Programming Talk
---

### Post by phrostbyte on 2008-09-11
The **League of Scripters** is a group of people who develop small interpreted programs known as "scripts" that accomplish specific and interesting tasks. Team members should be knowledgeable in at least one of the following: POSIX scripting (think Bash, sh, etc.), Python, TCL, Perl, or Ruby.

The League of Scripters has a new group on Launchpad
[http://launchpad.net/~scripters](http://launchpad.net/~scripters)

The League of Scripters also maintain the Community Script repository at [http://launchpad.net/scripting](http://launchpad.net/scripting), and have upload access to it. They also get a cute icon on their launchpad pages

The only requirement to join this group is be knowledgeable in one of the above languages, and have at least one script to submit to the repository.

---

### Post by mssever on 2008-09-11
> **phrostbyte said:**
> The **League of Scripters** is a group of people who develop small interpreted programs known as "scripts" that accomplish specific and interesting tasks. Team members should be knowledgeable in at least one of the following: POSIX scripting (think Bash, sh, etc.), Python, TCL, Perl, or Ruby.

The League of Scripters has a new group on Launchpad
[http://launchpad.net/~scripters]("http://launchpad.net/%7Escripters")

The League of Scripters also maintain the Community Script repository at [http://launchpad.net/scripting](http://launchpad.net/scripting), and have upload access to it. They also get a cute icon on their launchpad pages

The only requirement to join this group is be knowledgeable in one of the above languages, and have at least one script to submit to the repository.
Is there a way to simply drop scripts without worrying with bzr? I have several scripts that I don't need to bother with version control, but that I'm still willing to submit.

---

### Post by phrostbyte on 2008-09-11
Sure just post them in this thread with what license you want them in (GPLv3, MIT, BSD, Public Domain), and if you want to be credited in a certain way (eg: your real name, if you want).

---

### Post by drubin on 2008-09-11
Does php count? 

If yes count me in.

---

### Post by phrostbyte on 2008-09-11
Actually PHP should be fine, as it's possible to automate small tasks with it. I'm looking to start a group of people who like writing small, highly personalized or specialized programs. The kind of person who sees something they do repetitively and decide, hey, this is a good idea for a new script. So anyone who fits this bill is welcome to apply. You will be approved but I do ask that you submit at least one script to the public as open source (preferable under licenses compatible with the repository). You can post it here, put it on BZR yourself (I am aware not many people know how to use BZR, that's OK), or on your website, whatever. :)

---

### Post by drubin on 2008-09-11
Joined as "drubin" I will post some scripts when I work out how to use the site to add code.

---

### Post by phrostbyte on 2008-09-11
> **rubinboy said:**
> Joined as "drubin" I will post some scripts when I work out how to use the site to add code.

Learning how to use BZR or any source control is a bit complicated the first time you do it, but after you do it for the first time and get everything set up it's a incredibly simple and it's **sooooooo** worth learning! There is plenty of documentation on the net on how to use BZR too.

For reference the BZR trunk URL is bzr+ssh://your_user_id@bazaar.launchpad.net/~scripters/scripting/trunk

Replace your_user_id with your user id.

Thanks! :guitar:

---

### Post by phrostbyte on 2008-09-11
The commands to upload scripts to the tree yourself is something like:

```

mkdir scripting
bzr checkout lp:~scripters/scripting/trunk
<now add any scripts you want to add>
bzr add
bzr commit -m "<a message describing your changes>"
bzr push bzr+ssh://your_user_id@bazaar.launchpad.net/~scripters/scripting/trunk

```

---

### Post by drubin on 2008-09-11
I have never used BZR much but i have used SVN/CVS but was more talking about the structure of the tunk.

How are we arranging the different categorizes/projects/scripting langs.

---

### Post by stevescripts on 2008-09-11
phrostbyte - hmm ... I am somewhat familiar with CVS, SVN, CVSTrac, and fossil, but 
I must be really dense (tired tonight?) ... I don't see any scripts?

Do I need to join, login, or am I (highly likely) overlooking something simple?

---

### Post by mssever on 2008-09-12
> **stevescripts said:**
> phrostbyte - hmm ... I am somewhat familiar with CVS, SVN, CVSTrac, and fossil, but 
I must be really dense (tired tonight?) ... I don't see any scripts?

Do I need to join, login, or am I (highly likely) overlooking something simple?
To checkout:
```
bzr branch lp:scripting
```Commits are local. You have to push your changes after committing them to make them visible to others. ```
bzr commit -m 'Commit message'
bzr push lp:scripting # You have to join the group before you can push to lp:scripting
```If you get an error when trying to push, do ```
bzr launchpad-login your_launchpad_username
```

---

### Post by SeanHodges on 2008-09-12
Cool idea, there are some neat scripts in here already!

I have some bash/python/perl scripts ready for upload, soon as I'm approved to the team.

---

### Post by phrostbyte on 2008-09-13
Thanks guys for uploading the scripts. The repository is growing rapidly and a lot of you made some very useful scripts. It's looking very good now. I standardized some of the headers so maybe we will have some standard way to view metadata about the scripts functionality in the future. This can grow to something really nice. :)

---

### Post by phrostbyte on 2008-09-13
> **stevescripts said:**
> phrostbyte - hmm ... I am somewhat familiar with CVS, SVN, CVSTrac, and fossil, but 
I must be really dense (tired tonight?) ... I don't see any scripts?

Do I need to join, login, or am I (highly likely) overlooking something simple?

Changes can be viewed here:
[https://code.launchpad.net/~scripters/scripting/trunk](https://code.launchpad.net/~scripters/scripting/trunk)

Source code can be viewed here and individual scripts downloaded:
[http://bazaar.launchpad.net/~scripters/scripting/trunk/files](http://bazaar.launchpad.net/~scripters/scripting/trunk/files)

The whole tree can be pulled using bzr (sudo apt-get install bzr) as so:
```
bzr checkout lp:scripting
```

After you set yourself up with SSH keys and whatever on launchpad (there is how-tos on the net for this process if you get stuck), you can then commit using the following command
```

bzr add
bzr commit -m "Some message describing your changes"
```

It will be immediately uploaded back to launchpad after that. 

Actually you gain some "Karma points" for doing this, and I think once you get 10,000 of these points you get a "special surprise".

---

### Post by gvartser on 2008-09-13
Hi all, i just joined and got approved. Ill upload some nice scripts when im at home. Work do not allow outside communication..

/g

---

### Post by signifer123 on 2008-09-13
I couldn't figure out how to message from launchpad. But we should probably figure out a layout, or some organization for where we should put certain scripts. I'm not sure if that's what the message attached to commit #14 was reffering to, but i feel it's a good idea.

---

### Post by phrostbyte on 2008-09-15
> **signifer123 said:**
> I couldn't figure out how to message from launchpad. But we should probably figure out a layout, or some organization for where we should put certain scripts. I'm not sure if that's what the message attached to commit #14 was reffering to, but i feel it's a good idea.

The folders are pretty arbitrary, but here is a good guideline:

utility - Scripts that accomplish some kind of automated task
info - Scripts that display or organize information
install - Scripts that install software
vcs - version control related scripts

You can also add your own directories if you script doesn't make sense in one of these other directories. 

It's also good if you put the title and description of the script somewhere in the header because in the future we might have a sort of script package manager, and we can automate grabbing this metadata from the headers if they are consistent. You can take a look at the scripts in info right now for an idea of how the headers should look.

---

### Post by SeanHodges on 2008-09-22
mssever,

I like the gvim wrapper you put in the repo, and have made some modifications to make it work with plain old vim. I also added an option to clear the sudo timestamp each time for enhanced security (or enhanced annoyance, hence being an option ;)

I don't know what the best practices for modifying other peoples scripts are right now, so wanted to check before I pushed anything to Launchpad...

I've attached diffs of my changes.

---

### Post by SeanHodges on 2008-09-22
<Deleted by poster>

---

### Post by SeanHodges on 2008-09-22
Couple of fixes on top of the patches I gave, I posted a bit early!

---

### Post by mssever on 2008-09-22
As far as I'm concerned, go ahead and commit the changes, since they don't break existing functionality. My scripts were written with my needs in mind with no thought for what other people might want. Now that they're getting shared, it's only reasonable to make them more flexible.

I find it interesting to see how your use case for this script apparently differs from mine. For example, I have sudo configured to never ask for a password, since I find sudo's password prompts annoying and don't believe they do anything to enhance security--which is an opposite philosophy from running sudo -k in the script. So my workflow now involved my not havint to type sudo or enter a password when I want to edit a file--which would probably cause problems for those who have a habit of editing random files without understanding the consequences. I'm not saying this as a criticism; just an observation.

---

### Post by SeanHodges on 2008-09-22
mssever, thanks I'll submit my changes when I get chance.

I'll give you a bit of background on my interest in the script:

The convenience your script provides me is to prevent accidentally editing system files in Vim while in read-only mode. At the same time, I wanted to maintain a level of security against inadvertently modifying system files; which Vim's read-only mode usually provides.

This fixes a big complaint from my work colleagues about the mandated use of sudo on our shared Debian server. I wanted provide them with an alternative to incessantly using "sudo -s" because they had on previous occasions modified a system file, without prefixing sudo, and had to cancel their changes.

---

### Post by bobbocanfly on 2008-09-22
Just applied. Got an awesome bash script that acts as an mp3 player using gstreamer. Also some of those scripts could do with a cleanup!

---

### Post by phrostbyte on 2008-09-24
> **SeanHodges said:**
> mssever,

I like the gvim wrapper you put in the repo, and have made some modifications to make it work with plain old vim. I also added an option to clear the sudo timestamp each time for enhanced security (or enhanced annoyance, hence being an option ;)

I don't know what the best practices for modifying other peoples scripts are right now, so wanted to check before I pushed anything to Launchpad...

I've attached diffs of my changes.

Well since all the scripts uploaded to the repository should be under open source licenses, modifying someone else's script is okay. Make sure if they have credit for writing the script you don't remove it. :) (But you can add to it.) For an example of this you can look at the sysinfo script under info.

---

