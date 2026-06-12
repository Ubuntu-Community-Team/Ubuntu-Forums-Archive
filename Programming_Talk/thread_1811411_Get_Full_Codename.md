---
title: "Get Full Codename?"
date: 2011-07-24
forum: Programming Talk
---

### Post by qyot27 on 2011-07-24
One of my scripts takes the output of cat /etc/lsb-release and formats it for display elsewhere, but the codename field only responds with the adjective.  Is there any other method available to get the full "Adjective Animal" codename, or am I just going to have to continue updating the script with the codenames manually with each version release?

---

### Post by AlphaLexman on 2011-07-24
> **qyot27 said:**
> One of my scripts takes the output of cat /etc/lsb-release and formats it for display elsewhere, but the codename field only responds with the adjective.  Is there any other method available to get the full "Adjective Animal" codename, or am I just going to have to continue updating the script with the codenames manually with each version release?
```
lsb_release -cs | sed -e 's/natty/natty narwhal/g' \
	-e 's/maverick/maverick meerkat/g' \
	-e 's/lucid/lucid lynx/g' \
	-e 's/karmic/karmic koala/g' \
	-e 's/jaunty/jaunty jackalope/g'
```

---

### Post by qyot27 on 2011-07-25
That's the solution I was asking about avoiding.  Every time the OS updates, I'd have to add more or amend the aliases, which I don't want to have to do.  I want to be able to call a standard system utility or similar method that will give me all of that information so that it doesn't depend on me to specifically support it.

In other words, when Oneiric or 12.04 or 12.10 comes out, it will report their entire codenames automatically, without me needing to add the animal into it.  The only way to make sure of that is finding some system info file or utility that provides both the adjective and animal codename fields, or at least the animal field, since lsb-release has the adjective already.  I know how to take it from there.

---

### Post by drs305 on 2011-07-25
This was an interesting puzzle.

I did a search and found that in each Ubuntu release going back to at least Hardy contains a file /usr/share/python-apt/templates/Ubuntu.info
Example:
Description: Ubuntu 11.10 'Oneiric Ocelot'

That file contains the names of it's and previous releases. So if you identify your current release (I used 'lsb-release') you can extract the name. 

Here are the commands I used:

```
release=`lsb_release -r | cut -d ':' -f2`
```
Returns: **11.10**  and assigns to variable *release* (as an example)

```
grep $release /usr/share/python-apt/templates/Ubuntu.info | grep -m 1 "Description: Ubuntu " | cut -d "'" -f2
```
Returns: **Oneiric Ocelot**

Of course, you could create and store a much simpler file than /usr/share/python-apt/templates/Ubuntu.info and extract the codename from it by referencing the version number.

Disclaimer: I'm not a coder and have no idea if this is an efficient way of doing it, but it does provide the name in the format you wish. You would just add a *variable=* at the start of the second command to use it in your other commands.

---

### Post by Habitual on 2011-07-25
> **drs305 said:**
> ```
grep $release /usr/share/python-apt/templates/Ubuntu.info | grep -m 1 "Description: Ubuntu " | cut -d "'" -f2
```
...
Disclaimer: I'm not a coder and have no idea if this is an efficient way of doing it...

That is one fine piece of detective work for a "non-coder".

Props.

---

### Post by qyot27 on 2011-07-25
> **drs305 said:**
> This was an interesting puzzle.

I did a search and found that in each Ubuntu release going back to at least Hardy contains a file /usr/share/python-apt/templates/Ubuntu.info
Example:
Description: Ubuntu 11.10 'Oneiric Ocelot'

That file contains the names of it's and previous releases. So if you identify your current release (I used 'lsb-release') you can extract the name. 

Here are the commands I used:

```
release=`lsb_release -r | cut -d ':' -f2`
```
Returns: **11.10**  and assigns to variable *release* (as an example)

```
grep $release /usr/share/python-apt/templates/Ubuntu.info | grep -m 1 "Description: Ubuntu " | cut -d "'" -f2
```
Returns: **Oneiric Ocelot**

Of course, you could create and store a much simpler file than /usr/share/python-apt/templates/Ubuntu.info and extract the codename from it by referencing the version number.

Disclaimer: I'm not a coder and have no idea if this is an efficient way of doing it, but it does provide the name in the format you wish. You would just add a *variable=* at the start of the second command to use it in your other commands.
Thanks, that works swimmingly.  I'm sure there's also a more streamlined method of culling it all in one piece, but the resulting script is now:

```
#!/bin/bash
codenumber=`lsb_release -ds`
release=`lsb_release -rs`
codename=`grep $release /usr/share/python-apt/templates/Ubuntu.info | grep -m 1 "Description: Ubuntu " | cut -d "'" -f2`
echo $codenumber \"$codename\"
```

Which returns:
```
Ubuntu 11.04 "Natty Narwhal"
```

---

