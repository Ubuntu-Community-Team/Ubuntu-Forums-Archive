---
title: "Safe to redirect bash stdout to a shell subprocess (specifically, 'tee')?"
date: 2014-05-22
forum: Programming Talk
---

### Post by steeldriver on 2014-05-22
This was prompted by [this question on askubuntu.com]("http://askubuntu.com/q/470752/178692")

Can we safely redirect stdout to a tee subprocess - kind of like a poor man's 'script' without capturing the input keystrokes (and without the ANSI sequences which seem to cause headaches in color terms). Or is this a real no-no? What I'm thinking of specifically is:

```
exec 3>&1
```

to save the current standard output file descriptor, then

```
exec 1> >(tee -a outfile)
```

From this point on, standard output gets redirected to a `tee` subprocess that appends everything to `outfile`. Because we haven't redirected the subprocess's output stream, command output still appears in the terminal just as though it hadn't been redirected.

Once you're done with the commands whose output you want to capture, you can reverse the redirect and close the temporary file descriptor

```
exec 1>&3 3>&-
```

(actually I'm not sure if the 3>&- is required, since maybe we didn't actually open 3?) after which you can look in `outfile` to see the outputs of the commands...

Thoughts please! I'm reluctant to throw myself to the wolves by posting it on askubuntu :)

---

### Post by Vaphell on 2014-05-22
i don't know much about the exec voodoo, either way this article claims that you need named pipes for that.

[http://www.xensoft.com/content/use-exec-direct-all-bash-script-output-file-syslog-or-other-command](http://www.xensoft.com/content/use-exec-direct-all-bash-script-output-file-syslog-or-other-command)

---

### Post by steeldriver on 2014-05-22
Thanks Vaphell - always value your input on these things. I did see another reference that seemed to suggest the bash implementation used a FIFO under the hood if the platform supported it.

Anyhow I have posted it on askubuntu (with suitable disclaimers) so we'll see what the jury thinks ...

---

