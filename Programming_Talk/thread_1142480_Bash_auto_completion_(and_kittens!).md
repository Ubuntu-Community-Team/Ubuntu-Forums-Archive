---
title: "Bash auto completion (and kittens!)"
date: 2009-04-29
forum: Programming Talk
---

### Post by Steve DL on 2009-04-29
Hello people,

I'm currently writing a command line BitTorrent client, and I wish to use bash's auto completion for passing arguments to the client.

At the moment, I managed to get a list of parameters recognised by auto-completion, what I'm trying to do now is to define a list of available arguments depending on the previously written one. For instance :

kittentorrent resume <here goes a list of chosen parameters> Ideally, i'd like to filter the file auto completion so that it would only return the files in ~/.kitten/torrents/ ending with .torrent, but I tried and failed, so i guess there's an easier way to do so.

I'm a total noob with Bash tho, so I really don't know how. If there's any happy Bash hacker around who's willing to help me, he/she will get his name quoted on the client's credit for his/her contribution.

Btw : sorry, this wasn't about kittens as mentionned in the title, it was just to make people interested in reading the post :]

---

### Post by iiska on 2009-05-14
Maybe something like this could do the trick:

```
_kittens() {
	local cur files

	[ -r ~/.kitten/torrents/ ] || return 0

	COMPREPLY=()

        # Last word user was typing
	cur=${COMP_WORDS[COMP_CWORD]}

        # Match the command name of the application
        case ${COMP_WORDS[1]} in
        resume)
                # get the torrent files from the home dir.
	        files=$(\ls --color=none ~/.kitten/torrents/*.torrent)
                COMPREPLY=( $(compgen -o filenames -W "$files" -- $cur) )
                ;;
        *)
                # Some default stuff if second word doesn't match any commands
                ;;
        esac

	return 0
}
complete -F _kittens kittentorrent
```

Didn't really test that, but I think it should be somewhat OK. ;)

---

