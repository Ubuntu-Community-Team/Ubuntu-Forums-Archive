---
title: "Server 10.10 - Reprepro signing problem with gpg-agent"
date: 2011-06-28
forum: Packaging and Compiling Programs
---

### Post by ettech on 2011-06-28
Hi, 

So I'm trying to setup a Lan repo with custom packages using Reprepro. I can compile some packages, but when I try to add them to the repo, I get:

"Exporting indices...
Could not find any key matching 'XXXXXX'!
ERROR: Could not finish exporting 'maverick'!
This means that from outside your repository will still look like before (and
should still work if this old state worked), but the changes intended with this
call will not be visible until you call export directly (via reprepro export)
Changes will also get visible when something else changes the same file and
thus creates a new export of that file, but even changes to other parts of the
same distribution will not!
There have been errors!"

(I did a gpg --gen-key earlier that was successful).
I don't have any proof, but I feel this is related to gpg-agent somehow.. It wasn't installed.. I did the apt-get install gpg-agent and got it installed, but I don't think it's starting properly.
since it's a server, there's no .xsession, so I added the following to .bashrc

export GPGKEY=XXXXXXX
 if [ ! -f "${HOME}/.gpg-agent-info" ]; then
      gpg-agent --daemon --enable-ssh-support --write-env-file "${HOME}/.gpg-agent-info
     fi
 if [ -f "${HOME}/.gpg-agent-info" ]; then
       . "${HOME}/.gpg-agent-info"
       export GPG_AGENT_INFO
       export SSH_AUTH_SOCK
     fi
GPG_TTY=$(tty)
export GPG_TTY


sometimes it seems like I'm making progress, cause I get a "gpgme gave error GPGME:11:  Bad passphrase" error.


Any advice, tips or solutions would be greatly appreciated. Thanks!

---

