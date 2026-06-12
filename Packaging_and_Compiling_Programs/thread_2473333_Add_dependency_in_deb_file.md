---
title: "Add dependency in deb file"
date: 2022-04-01
forum: Packaging and Compiling Programs
---

### Post by pol2095 on 2022-04-01
Hello,

my app for working need

```
sudo add-apt-repository universe
sudo apt-get update
sudo apt-get install libleptonica-dev

```
is-it possible to add this depency in a *.deb file ?

Thanks.

---

### Post by Frogs Hair on 2022-04-01
That package is available in the repository,is there a particular version of the package you need ?

---

### Post by mIk3_08 on 2022-04-01
> **pol2095 said:**
> Hello,

my app for working need

```
sudo add-apt-repository universe
sudo apt-get update
sudo apt-get install libleptonica-dev

```
is-it possible to add this depency in a *.deb file ?

Thanks.
You can easily add dependency via command in terminal. Just specify the dependency you need. Good luck and cheers.

---

### Post by pol2095 on 2022-04-01
Is-it possible to add it when I package my app in the deb file ?

---

### Post by Frogs Hair on 2022-04-01
You should be able to add the dependency/s when creating your package.

---

### Post by mIk3_08 on 2022-04-02
> **pol2095 said:**
> Is-it possible to add it when I package my app in the deb file ?
> **Frogs Hair said:**
> You should be able to add the dependency/s when creating your package.
Yes. Frogs Hair is right. you should add dependency/s when creating a package. Just make sure that you identify/specify the dependency you add that suits to the package you have.

---

### Post by pol2095 on 2022-04-02
How to add the dependency when creating the package ? in the [COLOR=#5F6368][FONT=arial]**control**[/FONT][/COLOR][COLOR=#4D5156][FONT=arial] file ?
are-you a control file example ?[/FONT][/COLOR]

---

### Post by pol2095 on 2022-04-03
I tried this [example]("https://stackoverflow.com/a/70944293/12831451") using postinst file :
```

((
        # wait for install to finish
        while pgrep -x 'dpkg|apt|apt-get' > /dev/null; do sleep 1; done
        export DEBIAN_FRONTEND=noninteractive
        # make sure no one else is locking the dpkg database
        flock --exclusive --close /var/lib/dpkg/lock \
                sudo add-apt-repository universe
                sudo apt-get update
                sudo apt-get install libleptonica-dev
) 2>&1 >/dev/null </dev/null &)

```

but it doesn't work

I doesn't understand the last line

---

### Post by pol2095 on 2022-04-08
I think it's not possible with deb file, I tried in Fedora rpm install my dependency "libleptonica-dev" when I double-click on the rpm file.

---

### Post by Rocket2DMn on 2022-04-09
Debian packages can specify dependencies, though I don't think they'll automatically install when you install the deb package manually (using dpkg or "double clicking" from the desktop).  That's one reason we use package managers like apt, which automatically get dependencies for packages when installing from repositories.

Debian packaging can be rather complicated.  Have a look at the upstream packaging documentation for starters - [https://wiki.debian.org/Packaging/Intro](https://wiki.debian.org/Packaging/Intro).

The postinst approach you used doesn't seem appropriate, but to answer your question about it - the last line is just ignoring all output from the commands and effectively disallowing other input.

---

### Post by pol2095 on 2022-05-06
...

---

### Post by pol2095 on 2022-05-06
the dependencies are only installed in this case

> sudo dpkg -i myApp.deb
sudo apt-get install -f -y


it work only using command line but not ""double clicking" on the deb file

---

### Post by Rocket2DMn on 2022-05-08
If your Debian package has a dependency, you add to the "Depends" field under the "Package" specification in the debian/control file, as shown in the wiki link i provided earlier.  I believe that's the answer to your original question.  You do NOT re-package the dependency in your file, nor should you do this sort of dependency management in a postinst script (even the StackOverflow answer you linked to says you shouldn't do this).

If you want a solution that doesn't rely on package managers to help with dependencies, then you should look at "snap" packaging.  I've never created snap packages myself and I have some philosophical objections to its approach, but it's an alternative packaging tool to at least be aware of.

Cheers.

---

### Post by pol2095 on 2022-05-24
"Depends" only displays a message : "can't install the app, you need a dependency" but the dependency is never installed...

---

### Post by Rocket2DMn on 2022-05-24
A deb package declares its dependencies, but as far as I know, double-clicking a deb file (or using dpkg in the terminal) will never install those dependencies.  It can't because the deb installer doesn't know where to get those dependencies from.  This is what package managers like apt are for - they know where to get packages in the configured repositories (e.g., those specified in /etc/apt/sources.list).

If you're not publishing your package in a repository where a package manager installs from, then you need to instruct users to first install your deb file's dependencies before they try to install the deb file.

---

### Post by ajgreeny on 2022-05-24
Have you tried the command
***sudo apt install /path/to/filename.deb***
which normally manages to download all dependencies for .deb packages, assuming, of course, that those dependencies are spelled out in the control file and are available in the repos.

Unkile dpkg apt, but not as far as I'm aware apt-get will manage dependencies very well, as gdebi does, or did the last time I used it.

---

### Post by #&amp;thj^% on 2022-05-24
> **ajgreeny said:**
> 
Unkile dpkg apt, but not as far as I'm aware apt-get will manage dependencies very well, as gdebi does, or did the last time I used it.

Long time gdebi user, and still handles deps 98% effectively.

---

### Post by ajgreeny on 2022-05-24
> **1fallen said:**
> Long time gdebi user, and still handles deps 98% effectively.

I used it a lot in the past but now that apt does the same job I see no reason to bother with it.

---

