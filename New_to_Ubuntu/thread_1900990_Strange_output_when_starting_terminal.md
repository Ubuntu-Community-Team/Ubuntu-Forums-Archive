---
title: "Strange output when starting terminal"
date: 2011-12-27
forum: New to Ubuntu
---

### Post by AndyP79 on 2011-12-27
Hi Ya'll,
 Okay, so when I open the terminal, I get this output first, but I still seem to be able to install and do things from the terminal, any ideas what this is and can I fix it?
Thanks

bash: /dev/sda1: Permission denied
No command 'proc' found, did you mean:
 Command 'nproc' from package 'coreutils' (main)
 Command 'proj' from package 'proj-bin' (universe)
proc: command not found
sysfs: command not found
fusectl: command not found
No command 'none' found, did you mean:
 Command 'nona' from package 'hugin-tools' (universe)
 Command 'one' from package 'opennebula' (universe)
 Command 'note' from package 'note' (universe)
 Command 'cone' from package 'cone' (universe)
 Command 'node' from package 'node' (universe)
 Command 'node' from package 'nodejs' (universe)
none: command not found
No command 'none' found, did you mean:
 Command 'nona' from package 'hugin-tools' (universe)
 Command 'one' from package 'opennebula' (universe)
 Command 'note' from package 'note' (universe)
 Command 'cone' from package 'cone' (universe)
 Command 'node' from package 'node' (universe)
 Command 'node' from package 'nodejs' (universe)
none: command not found
No command 'udev' found, did you mean:
 Command 'udv' from package 'ncbi-tools-x11' (universe)
 Command 'udav' from package 'udav' (universe)
 Command 'udevd' from package 'udev' (main)
udev: command not found
devpts: command not found
No command 'tmpfs' found, did you mean:
 Command 'mtpfs' from package 'mtpfs' (universe)
tmpfs: command not found
No command 'none' found, did you mean:
 Command 'nona' from package 'hugin-tools' (universe)
 Command 'one' from package 'opennebula' (universe)
 Command 'note' from package 'note' (universe)
 Command 'cone' from package 'cone' (universe)
 Command 'node' from package 'node' (universe)
 Command 'node' from package 'nodejs' (universe)
none: command not found
No command 'none' found, did you mean:
 Command 'nona' from package 'hugin-tools' (universe)
 Command 'one' from package 'opennebula' (universe)
 Command 'note' from package 'note' (universe)
 Command 'cone' from package 'cone' (universe)
 Command 'node' from package 'node' (universe)
 Command 'node' from package 'nodejs' (universe)
none: command not found
binfmt_misc: command not found
gvfs-fuse-daemon: command not found
bash: .: /etc/bash_completion.d/iftop: cannot execute binary file

---

### Post by TeoBigusGeekus on 2011-12-27
Check your ~/.bashrc file.

---

### Post by AndyP79 on 2011-12-27
> **TeoBigusGeekus said:**
> Check your ~/.bashrc file.

Cool..... uh.... sorry, but not sure where to find it, and when I do, what am I looking for?

---

### Post by collisionystm on 2011-12-27
> **AndyP79 said:**
> Cool..... uh.... sorry, but not sure where to find it, and when I do, what am I looking for?

cat ~/.bashrc

post output

---

### Post by Sempa on 2011-12-27
> **AndyP79 said:**
> Cool..... uh.... sorry, but not sure where to find it, and when I do, what am I looking for?
It's my understanding that the .bashrc file located in your home folder contains a lot of commands that are run automatically when an interactive bash shell is started.
You should probably be looking for lines containing *proc*, *nproc*, *proj*, and all the other commands that couldn't be found.

---

### Post by bodhi.zazen on 2011-12-28
> **collisionystm said:**
> cat ~/.bashrc

post output

can be simplified

```
cat ~/.bashrc | pastebinit
```

[https://help.ubuntu.com/community/Pastebinit](https://help.ubuntu.com/community/Pastebinit)

May need to install pastebinit first

```
sudo apt-get install pastebinit
```

---

### Post by jtarin on 2011-12-28
Your .bash.rc file is a very simple file......offhand it would seem as if your $PATH variables are not set properly.Run and post the results of the command  ```
echo $PATH
```

---

### Post by AndyP79 on 2011-12-28
> **collisionystm said:**
> cat ~/.bashrc

post output


Okay, here is this one

# ~/.bashrc: executed by bash(1) for non-login shells.
# see /usr/share/doc/bash/examples/startup-files (in the package bash-doc)
# for examples

# If not running interactively, don't do anything
[ -z "$PS1" ] && return

# don't put duplicate lines in the history. See bash(1) for more options
# ... or force ignoredups and ignorespace
HISTCONTROL=ignoredups:ignorespace

# append to the history file, don't overwrite it
shopt -s histappend

# for setting history length see HISTSIZE and HISTFILESIZE in bash(1)
HISTSIZE=1000
HISTFILESIZE=2000

# check the window size after each command and, if necessary,
# update the values of LINES and COLUMNS.
shopt -s checkwinsize

# make less more friendly for non-text input files, see lesspipe(1)
[ -x /usr/bin/lesspipe ] && eval "$(SHELL=/bin/sh lesspipe)"

# set variable identifying the chroot you work in (used in the prompt below)
if [ -z "$debian_chroot" ] && [ -r /etc/debian_chroot ]; then
    debian_chroot=$(cat /etc/debian_chroot)
fi

# set a fancy prompt (non-color, unless we know we "want" color)
case "$TERM" in
    xterm-color) color_prompt=yes;;
esac

# uncomment for a colored prompt, if the terminal has the capability; turned
# off by default to not distract the user: the focus in a terminal window
# should be on the output of commands, not on the prompt
#force_color_prompt=yes

if [ -n "$force_color_prompt" ]; then
    if [ -x /usr/bin/tput ] && tput setaf 1 >&/dev/null; then
	# We have color support; assume it's compliant with Ecma-48
	# (ISO/IEC-6429). (Lack of such support is extremely rare, and such
	# a case would tend to support setf rather than setaf.)
	color_prompt=yes
    else
	color_prompt=
    fi
fi

if [ "$color_prompt" = yes ]; then
    PS1='${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]\$ '
else
    PS1='${debian_chroot:+($debian_chroot)}\u@\h:\w\$ '
fi
unset color_prompt force_color_prompt

# If this is an xterm set the title to user@host:dir
case "$TERM" in
xterm*|rxvt*)
    PS1="\[\e]0;${debian_chroot:+($debian_chroot)}\u@\h: \w\a\]$PS1"
    ;;
*)
    ;;
esac

# enable color support of ls and also add handy aliases
if [ -x /usr/bin/dircolors ]; then
    test -r ~/.dircolors && eval "$(dircolors -b ~/.dircolors)" || eval "$(dircolors -b)"
    alias ls='ls --color=auto'
    #alias dir='dir --color=auto'
    #alias vdir='vdir --color=auto'

    alias grep='grep --color=auto'
    alias fgrep='fgrep --color=auto'
    alias egrep='egrep --color=auto'
fi

# some more ls aliases
alias ll='ls -alF'
alias la='ls -A'
alias l='ls -CF'

# Add an "alert" alias for long running commands.  Use like so:
#   sleep 10; alert
alias alert='notify-send --urgency=low -i "$([ $? = 0 ] && echo terminal || echo error)" "$(history|tail -n1|sed -e '\''s/^\s*[0-9]\+\s*//;s/[;&|]\s*alert$//'\'')"'

# Alias definitions.
# You may want to put all your additions into a separate file like
# ~/.bash_aliases, instead of adding them here directly.
# See /usr/share/doc/bash-doc/examples in the bash-doc package.

if [ -f ~/.bash_aliases ]; then
    . ~/.bash_aliases
fi

# enable programmable completion features (you don't need to enable
# this, if it's already enabled in /etc/bash.bashrc and /etc/profile
# sources /etc/bash.bashrc).
if [ -f /etc/bash_completion ] && ! shopt -oq posix; then
    . /etc/bash_completion
fi

---

### Post by AndyP79 on 2011-12-28
> **jtarin said:**
> Your .bash.rc file is a very simple file......offhand it would seem as if your $PATH variables are not set properly.Run and post the results of the command  ```
echo $PATH
```


And here is this one


/usr/lib/lightdm/lightdm:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games

---

### Post by AndyP79 on 2011-12-28
By the way folks, I am using 11.10 32 bit on an amd64 bit machine, don't know if that matters or not?
Thanks for the help so far also:D

---

### Post by bodhi.zazen on 2011-12-28
so it is not your .bashrc, check the files you are sourcing 

. ~/.bash_aliases

---

### Post by collisionystm on 2011-12-28
post the output of


ls /etc/bash_completion.d/


^ That is LS not is

---

### Post by AndyP79 on 2011-12-28
> **bodhi.zazen said:**
> so it is not your .bashrc, check the files you are sourcing 

. ~/.bash_aliases

andrew@dirkpitt:~$ . ~/.bash_aliases
bash: /home/andrew/.bash_aliases: No such file or directory

---

### Post by AndyP79 on 2011-12-28
> **collisionystm said:**
> post the output of


ls /etc/bash_completion.d/


^ That is LS not is

abook                    iconv              povray
ant                      iftop              procps
apache2ctl               ifupdown           python
apport_completion        imagemagick        qdbus
apt                      info               qemu
apt-build                initramfs-tools    quota-tools
aptitude                 insserv            rcs
aspell                   ipmitool           rdesktop
autoconf                 iproute2           reportbug
automake                 ipsec              resolvconf
autorpm                  iptables           rfkill
axi-cache                ipv6calc           ri
bash-builtins            isql               rpcdebug
bind-utils               jar                rpm
bitkeeper                java               rpmcheck
bittorrent               k3b                rrdtool
bluez                    kldload            rsync
brctl                    larch              rtcwake
bzip2                    ldapvi             samba
cardctl                  lftp               sbcl
cfengine                 libreoffice.sh     screen
chkconfig                lilo               service
chsh                     links              sh
cksfv                    lintian            shadow
clisp                    lisp               sitecopy
configure                lrzip              smartctl
coreutils                lsof               snownews
cowsay                   lvm                sqlite3
cpan2dist                lzma               ssh
cpio                     lzop               sshfs
crontab                  mailman            strace
cryptsetup               make               svk
cups                     man                sysbench
cvs                      mc                 sysctl
cvsps                    mcrypt             sysv-rc
dd                       mdadm              tar
debconf                  medusa             tcpdump
desktop-file-validate    minicom            ufw
dhclient                 mkinitrd           unace
dict                     module-init-tools  unrar
dkms                     monodevelop        update-alternatives
dpkg                     mount              upstart
dselect                  mplayer            util-linux
dsniff                   msynctool          vncviewer
dvd+rw-tools             munin-node         vpnc
e2fsprogs                mutt               wireless-tools
findutils                mysqladmin         wodim
freeciv                  ncftp              wol
freerdp                  net-tools          wtf
fuse                     nmap               wvdial
gcc                      ntpdate            xhost
gcl                      open-iscsi         xm
gdb                      openldap           xmllint
genisoimage              openssl            xmlwf
getent                   p4                 xmms
gkrellm                  perl               xmodmap
gnatmake                 pine               xrandr
gpg                      pkg-config         xrdb
gpg2                     pkg_install        xsltproc
grub                     pkgtools           xz
gvfs-bash-completion.sh  pm-utils           yp-tools
gzip                     pon                yum-arch
heimdal                  portupgrade        zeitgeist-daemon
helpers                  postfix
hping2                   postgresql

---

### Post by collisionystm on 2011-12-28
getting warm....

post output of

cat /etc/bash_completion

---

### Post by AndyP79 on 2011-12-28
> **collisionystm said:**
> getting warm....

post output of

cat /etc/bash_completion

```
_known_hosts()
{
    local options
    COMPREPLY=()

    # NOTE: Using `_known_hosts' as a helper function and passing options
    #       to `_known_hosts' is deprecated: Use `_known_hosts_real' instead.
    [[ "$1" == -a || "$2" == -a ]] && options=-a
    [[ "$1" == -c || "$2" == -c ]] && options="$options -c"
    _known_hosts_real $options "$(_get_cword :)"
} # _known_hosts()

# Helper function for completing _known_hosts.
# This function performs host completion based on ssh's config and known_hosts
# files, as well as hostnames reported by avahi-browse if
# COMP_KNOWN_HOSTS_WITH_AVAHI is set to a non-empty value.  Also hosts from
# HOSTFILE (compgen -A hostname) are added, unless
# COMP_KNOWN_HOSTS_WITH_HOSTFILE is set to an empty value.
# Usage: _known_hosts_real [OPTIONS] CWORD
# Options:  -a             Use aliases
#           -c             Use `:' suffix
#           -F configfile  Use `configfile' for configuration settings
#           -p PREFIX      Use PREFIX
# Return: Completions, starting with CWORD, are added to COMPREPLY[]
_known_hosts_real()
{
    local configfile flag prefix
    local cur curd awkcur user suffix aliases i host
    local -a kh khd config

    local OPTIND=1
    while getopts "acF:p:" flag "$@"; do
        case $flag in
            a) aliases='yes' ;;
            c) suffix=':' ;;
            F) configfile=$OPTARG ;;
            p) prefix=$OPTARG ;;
        esac
    done
    [ $# -lt $OPTIND ] && echo "error: $FUNCNAME: missing mandatory argument CWORD"
    cur=${!OPTIND}; let "OPTIND += 1"
    [ $# -ge $OPTIND ] && echo "error: $FUNCNAME("$@"): unprocessed arguments:"\
    $(while [ $# -ge $OPTIND ]; do printf '%s\n' ${!OPTIND}; shift; done)

    [[ $cur == *@* ]] && user=${cur%@*}@ && cur=${cur#*@}
    kh=()

    # ssh config files
    if [ -n "$configfile" ]; then
        [ -r "$configfile" ] &&
        config=( "${config[@]}" "$configfile" )
    else
        for i in /etc/ssh/ssh_config "${HOME}/.ssh/config" \
            "${HOME}/.ssh2/config"; do
            [ -r $i ] && config=( "${config[@]}" "$i" )
        done
    fi

    # Known hosts files from configs
    if [ ${#config[@]} -gt 0 ]; then
        local OIFS=$IFS IFS=$'\n'
        local -a tmpkh
        # expand paths (if present) to global and user known hosts files
        # TODO(?): try to make known hosts files with more than one consecutive
        #          spaces in their name work (watch out for ~ expansion
        #          breakage! Alioth#311595)
        tmpkh=( $( awk 'sub("^[ \t]*([Gg][Ll][Oo][Bb][Aa][Ll]|[Uu][Ss][Ee][Rr])[Kk][Nn][Oo][Ww][Nn][Hh][Oo][Ss][Tt][Ss][Ff][Ii][Ll][Ee][ \t]+", "") { print $0 }' "${config[@]}" | sort -u ) )
        for i in "${tmpkh[@]}"; do
            # Remove possible quotes
            i=${i//\"}
            # Eval/expand possible `~' or `~user'
            __expand_tilde_by_ref i
            [ -r "$i" ] && kh=( "${kh[@]}" "$i" )
        done
        IFS=$OIFS
    fi

    if [ -z "$configfile" ]; then
        # Global and user known_hosts files
        for i in /etc/ssh/ssh_known_hosts /etc/ssh/ssh_known_hosts2 \
            /etc/known_hosts /etc/known_hosts2 ~/.ssh/known_hosts \
            ~/.ssh/known_hosts2; do
            [ -r $i ] && kh=( "${kh[@]}" $i )
        done
        for i in /etc/ssh2/knownhosts ~/.ssh2/hostkeys; do
            [ -d $i ] && khd=( "${khd[@]}" $i/*pub )
        done
    fi

    # If we have known_hosts files to use
    if [[ ${#kh[@]} -gt 0 || ${#khd[@]} -gt 0 ]]; then
        # Escape slashes and dots in paths for awk
        awkcur=${cur//\//\\\/}
        awkcur=${awkcur//\./\\\.}
        curd=$awkcur

        if [[ "$awkcur" == [0-9]*[.:]* ]]; then
            # Digits followed by a dot or a colon - just search for that
            awkcur="^$awkcur[.:]*"
        elif [[ "$awkcur" == [0-9]* ]]; then
            # Digits followed by no dot or colon - search for digits followed
            # by a dot or a colon
            awkcur="^$awkcur.*[.:]"
        elif [ -z "$awkcur" ]; then
            # A blank - search for a dot, a colon, or an alpha character
            awkcur="[a-z.:]"
        else
            awkcur="^$awkcur"
        fi

        if [ ${#kh[@]} -gt 0 ]; then
            # FS needs to look for a comma separated list
            COMPREPLY=( "${COMPREPLY[@]}" $( awk 'BEGIN {FS=","}
            /^\s*[^|\#]/ {for (i=1; i<=2; ++i) { \
            sub(" .*$", "", $i); \
            sub("^\\[", "", $i); sub("\\](:[0-9]+)?$", "", $i); \
            if ($i ~ /'"$awkcur"'/) {print $i} \
            }}' "${kh[@]}" 2>/dev/null ) )
        fi
        if [ ${#khd[@]} -gt 0 ]; then
            # Needs to look for files called
            # .../.ssh2/key_22_<hostname>.pub
            # dont fork any processes, because in a cluster environment,
            # there can be hundreds of hostkeys
            for i in "${khd[@]}" ; do
                if [[ "$i" == *key_22_$curd*.pub && -r "$i" ]]; then
                    host=${i/#*key_22_/}
                    host=${host/%.pub/}
                    COMPREPLY=( "${COMPREPLY[@]}" $host )
                fi
            done
        fi

        # apply suffix and prefix
        for (( i=0; i < ${#COMPREPLY[@]}; i++ )); do
            COMPREPLY[i]=$prefix$user${COMPREPLY[i]}$suffix
        done
    fi

    # append any available aliases from config files
    if [[ ${#config[@]} -gt 0 && -n "$aliases" ]]; then
        local hosts=$( sed -ne 's/^[ \t]*[Hh][Oo][Ss][Tt]\([Nn][Aa][Mm][Ee]\)\{0,1\}['"$'\t '"']\{1,\}\([^#*?]*\)\(#.*\)\{0,1\}$/\2/p' "${config[@]}" )
        COMPREPLY=( "${COMPREPLY[@]}" $( compgen  -P "$prefix$user" \
            -S "$suffix" -W "$hosts" -- "$cur" ) )
    fi

    # Add hosts reported by avahi-browse, if desired and it's available.

    # This feature is disabled because it does not scale to
    #  larger networks. See:
    # [https://bugs.launchpad.net/ubuntu/+source/bash-completion/+bug/510591](https://bugs.launchpad.net/ubuntu/+source/bash-completion/+bug/510591)

    #if [[ ${COMP_KNOWN_HOSTS_WITH_AVAHI:-} ]] && \
    #    type avahi-browse &>/dev/null; then
        # The original call to avahi-browse also had "-k", to avoid lookups
        # into avahi's services DB. We don't need the name of the service, and
        # if it contains ";", it may mistify the result. But on Gentoo (at
        # least), -k wasn't available (even if mentioned in the manpage) some
        # time ago, so...
    #    COMPREPLY=( "${COMPREPLY[@]}" $( \
    #        compgen -P "$prefix$user" -S "$suffix" -W \
    #        "$( avahi-browse -cpr _workstation._tcp 2>/dev/null | \
    #             awk -F';' '/^=/ { print $7 }' | sort -u )" -- "$cur" ) )
    #fi

    # Add results of normal hostname completion, unless
    # `COMP_KNOWN_HOSTS_WITH_HOSTFILE' is set to an empty value.
    if [ -n "${COMP_KNOWN_HOSTS_WITH_HOSTFILE-1}" ]; then
        COMPREPLY=( "${COMPREPLY[@]}"
            $( compgen -A hostname -P "$prefix$user" -S "$suffix" -- "$cur" ) )
    fi

    __ltrim_colon_completions "$prefix$user$cur"

    return 0
} # _known_hosts_real()
complete -F _known_hosts traceroute traceroute6 tracepath tracepath6 ping \
    ping6 fping fping6 telnet host nslookup rsh rlogin ftp dig mtr \
    ssh-installkeys showmount

# This meta-cd function observes the CDPATH variable, so that cd additionally
# completes on directories under those specified in CDPATH.
#
_cd()
{
    local cur IFS=$'\n' i j k
    _get_comp_words_by_ref cur

    # try to allow variable completion
    if [[ "$cur" == ?(\\)\$* ]]; then
        COMPREPLY=( $( compgen -v -P '$' -- "${cur#?(\\)$}" ) )
        return 0
    fi

    _compopt_o_filenames

    # Use standard dir completion if no CDPATH or parameter starts with /,
    # ./ or ../
    if [[ -z "${CDPATH:-}" || "$cur" == ?(.)?(.)/* ]]; then
        _filedir -d
        return 0
    fi

    local -r mark_dirs=$(_rl_enabled mark-directories && echo y)
    local -r mark_symdirs=$(_rl_enabled mark-symlinked-directories && echo y)

    # we have a CDPATH, so loop on its contents
    for i in ${CDPATH//:/$'\n'}; do
        # create an array of matched subdirs
        k="${#COMPREPLY[@]}"
        for j in $( compgen -d $i/$cur ); do
            if [[ ( $mark_symdirs && -h $j || $mark_dirs && ! -h $j ) && ! -d ${j#$i/} ]]; then
                j="${j}/"
            fi
            COMPREPLY[k++]=${j#$i/}
        done
    done

    _filedir -d

    if [[ ${#COMPREPLY[@]} -eq 1 ]]; then
        i=${COMPREPLY[0]}
        if [[ "$i" == "$cur" && $i != "*/" ]]; then
            COMPREPLY[0]="${i}/"
        fi
    fi

    return 0
}
if shopt -q cdable_vars; then
    complete -v -F _cd -o nospace cd
else
    complete -F _cd -o nospace cd
fi

# a wrapper method for the next one, when the offset is unknown
_command()
{
    local offset i

    # find actual offset, as position of the first non-option
    offset=1
    for (( i=1; i <= COMP_CWORD; i++ )); do
        if [[ "${COMP_WORDS[i]}" != -* ]]; then
            offset=$i
            break
        fi
    done
    _command_offset $offset
}

# A meta-command completion function for commands like sudo(8), which need to
# first complete on a command, then complete according to that command's own
# completion definition - currently not quite foolproof (e.g. mount and umount
# don't work properly), but still quite useful.
#
_command_offset()
{
    local cur func cline cspec noglob cmd i char_offset word_offset \
        _COMMAND_FUNC _COMMAND_FUNC_ARGS

    word_offset=$1

    # rewrite current completion context before invoking
    # actual command completion

    # find new first word position, then
    # rewrite COMP_LINE and adjust COMP_POINT
    local first_word=${COMP_WORDS[$word_offset]}
    for (( i=0; i <= ${#COMP_LINE}; i++ )); do
        if [[ "${COMP_LINE:$i:${#first_word}}" == "$first_word" ]]; then
            char_offset=$i
            break
        fi
    done
    COMP_LINE=${COMP_LINE:$char_offset}
    COMP_POINT=$(( COMP_POINT - $char_offset ))

    # shift COMP_WORDS elements and adjust COMP_CWORD
    for (( i=0; i <= COMP_CWORD - $word_offset; i++ )); do
        COMP_WORDS[i]=${COMP_WORDS[i+$word_offset]}
    done
    for (( i; i <= COMP_CWORD; i++ )); do
        unset COMP_WORDS[i];
    done
    COMP_CWORD=$(( $COMP_CWORD - $word_offset ))

    COMPREPLY=()
    _get_comp_words_by_ref cur

    if [[ $COMP_CWORD -eq 0 ]]; then
        _compopt_o_filenames
        COMPREPLY=( $( compgen -c -- "$cur" ) )
    else
        cmd=${COMP_WORDS[0]}
        if complete -p ${cmd##*/} &>/dev/null; then
            cspec=$( complete -p ${cmd##*/} )
            if [ "${cspec#* -F }" != "$cspec" ]; then
                # complete -F <function>

                # get function name
                func=${cspec#*-F }
                func=${func%% *}

                if [[ ${#COMP_WORDS[@]} -ge 2 ]]; then
                    $func $cmd "${COMP_WORDS[${#COMP_WORDS[@]}-1]}" "${COMP_WORDS[${#COMP_WORDS[@]}-2]}"
                else
                    $func $cmd "${COMP_WORDS[${#COMP_WORDS[@]}-1]}"
                fi

                # remove any \: generated by a command that doesn't
                # default to filenames or dirnames (e.g. sudo chown)
                # FIXME: I'm pretty sure this does not work!
                if [ "${cspec#*-o }" != "$cspec" ]; then
                    cspec=${cspec#*-o }
                    cspec=${cspec%% *}
                    if [[ "$cspec" != @(dir|file)names ]]; then
                        COMPREPLY=("${COMPREPLY[@]//\\\\:/:}")
                    else
                        _compopt_o_filenames
                    fi
                fi
            elif [ -n "$cspec" ]; then
                cspec=${cspec#complete};
                cspec=${cspec%%${cmd##*/}};
                COMPREPLY=( $( eval compgen "$cspec" -- "$cur" ) );
            fi
        elif [ ${#COMPREPLY[@]} -eq 0 ]; then
            _filedir
        fi
    fi
}
complete -F _command aoss command do else eval exec ltrace nice nohup padsp \
    then time tsocks vsound xargs

_root_command()
{
    local PATH=$PATH:/sbin:/usr/sbin:/usr/local/sbin
    local root_command=$1
    _command $1 $2 $3
}
complete -F _root_command fakeroot gksu gksudo kdesudo really sudo

# Return true if the completion should be treated as running as root
_complete_as_root()
{
    [[ $EUID -eq 0 || ${root_command:-} ]]
}

_longopt()
{
    local cur prev split=false
    _get_comp_words_by_ref -n = cur prev

    _split_longopt && split=true

    case "$prev" in
        --*[Dd][Ii][Rr]*)
            _filedir -d
            return 0
            ;;
        --*[Ff][Ii][Ll][Ee]*|--*[Pp][Aa][Tt][Hh]*)
            _filedir
            return 0
            ;;
    esac

    $split && return 0

    if [[ "$cur" == -* ]]; then
        COMPREPLY=( $( compgen -W "$( $1 --help 2>&1 | \
            sed -ne 's/.*\(--[-A-Za-z0-9]\{1,\}\).*/\1/p' | sort -u )" \
            -- "$cur" ) )
    elif [[ "$1" == @(mk|rm)dir ]]; then
        _filedir -d
    else
        _filedir
    fi
}
# makeinfo and texi2dvi are defined elsewhere.
for i in a2ps awk bash bc bison cat colordiff cp csplit \
    curl cut date df diff dir du enscript env expand fmt fold gperf gprof \
    grep grub head indent irb ld ldd less ln ls m4 md5sum mkdir mkfifo mknod \
    mv netstat nl nm objcopy objdump od paste patch pr ptx readelf rm rmdir \
    sed seq sha{,1,224,256,384,512}sum shar sort split strip tac tail tee \
    texindex touch tr uname unexpand uniq units vdir wc wget who; do
    have $i && complete -F _longopt -o default $i
done
unset i

_filedir_xspec()
{
    local IFS cur xspec

    IFS=$'\n'
    COMPREPLY=()
    _get_comp_words_by_ref cur

    _expand || return 0

    # get first exclusion compspec that matches this command
    xspec=$( awk "/^complete[ \t]+.*[ \t]${1##*/}([ \t]|\$)/ { print \$0; exit }" \
        "$BASH_COMPLETION" )
    # prune to leave nothing but the -X spec
    xspec=${xspec#*-X }
    xspec=${xspec%% *}

    local -a toks
    local tmp

    toks=( ${toks[@]-} $(
        compgen -d -- "$(quote_readline "$cur")" | {
        while read -r tmp; do
            # see long TODO comment in _filedir() --David
            printf '%s\n' $tmp
        done
        }
        ))

    # Munge xspec to contain uppercase version too
    eval xspec="${xspec}"
    local matchop=!
    if [[ $xspec == !* ]]; then
        xspec=${xspec#!}
        matchop=@
    fi
    [[ ${BASH_VERSINFO[0]} -ge 4 ]] && \
        xspec="$matchop($xspec|${xspec^^})" || \
        xspec="$matchop($xspec|$(printf %s $xspec | tr '[:lower:]' '[:upper:]'))"

    toks=( ${toks[@]-} $(
        eval compgen -f -X "!$xspec" -- "\$(quote_readline "\$cur")" | {
        while read -r tmp; do
            [ -n $tmp ] && printf '%s\n' $tmp
        done
        }
        ))

    [ ${#toks[@]} -ne 0 ] && _compopt_o_filenames
    COMPREPLY=( "${toks[@]}" )
}
list=( $( sed -ne '/^# START exclude/,/^# FINISH exclude/p' "$BASH_COMPLETION" | \
    # read exclusion compspecs
    (
    while read line
    do
        # ignore compspecs that are commented out
        if [ "${line#\#}" != "$line" ]; then continue; fi
        line=${line%# START exclude*}
        line=${line%# FINISH exclude*}
        line=${line##*\'}
        list=( "${list[@]}" $line )
    done
    printf '%s ' "${list[@]}"
    )
    ) )
# remove previous compspecs
if [ ${#list[@]} -gt 0 ]; then
    eval complete -r ${list[@]}
    # install new compspecs
    eval complete -F _filedir_xspec "${list[@]}"
fi
unset list

# source completion directory definitions
if [[ -d $BASH_COMPLETION_COMPAT_DIR && -r $BASH_COMPLETION_COMPAT_DIR && \
    -x $BASH_COMPLETION_COMPAT_DIR ]]; then
    for i in $(LC_ALL=C command ls "$BASH_COMPLETION_COMPAT_DIR"); do
        i=$BASH_COMPLETION_COMPAT_DIR/$i
        [[ ${i##*/} != @(*~|*.bak|*.swp|\#*\#|*.dpkg*|*.rpm@(orig|new|save)|Makefile*) \
            && -f $i && -r $i ]] && . "$i"
    done
fi
if [[ $BASH_COMPLETION_DIR != $BASH_COMPLETION_COMPAT_DIR && \
    -d $BASH_COMPLETION_DIR && -r $BASH_COMPLETION_DIR && \
    -x $BASH_COMPLETION_DIR ]]; then
    for i in $(LC_ALL=C command ls "$BASH_COMPLETION_DIR"); do
        i=$BASH_COMPLETION_DIR/$i
        [[ ${i##*/} != @(*~|*.bak|*.swp|\#*\#|*.dpkg*|*.rpm@(orig|new|save)|Makefile*) \
            && -f $i && -r $i ]] && . "$i"
    done
fi
unset i

# source user completion file
[[ $BASH_COMPLETION != ~/.bash_completion && -r ~/.bash_completion ]] \
    && . ~/.bash_completion
unset -f have
unset UNAME USERLAND have

set $BASH_COMPLETION_ORIGINAL_V_VALUE
unset BASH_COMPLETION_ORIGINAL_V_VALUE

# Local variables:
# mode: shell-script
# sh-basic-offset: 4
# sh-indent-comment: t
# indent-tabs-mode: nil
# End:
# ex: ts=4 sw=4 et filetype=sh
andrew@dirkpitt:~$
```

---

### Post by collisionystm on 2011-12-29
do this

sudo apt-get install chsh

chsh -s /bin/bash

close terminal

re-open

still get errors?

---

### Post by AndyP79 on 2011-12-29
> **collisionystm said:**
> do this

sudo apt-get install chsh

chsh -s /bin/bash

close terminal

re-open

still get errors?

andrew@dirkpitt:~$ sudo apt-get install chsh
[sudo] password for andrew: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package chsh


I did this, then did the second part and closed the terminal, still got the errors, I just pasted what the output was.

---

### Post by yetiman64 on 2011-12-30
chsh is a part of (a command within) the passwd package not a package itself, that would explain it not being found. I do suspect collisionystm **may** have meant the C shell package "csh". Please wait for collisionystm to confirm this.

---

### Post by collisionystm on 2011-12-30
> **yetiman64 said:**
> chsh is a part of (a command within) the passwd package not a package itself, that would explain it not being found. I do suspect collisionystm **may** have meant the C shell package "csh". Please wait for collisionystm to confirm this.


No my mistake

i thought he may need to install chsh


post the output of

cat /etc/bash_completion.d/mount

---

### Post by collisionystm on 2011-12-30
also post

cat /etc/initramfs-tools/initramfs.conf

---

### Post by AndyP79 on 2011-12-30
> **collisionystm said:**
> No my mistake

i thought he may need to install chsh


post the output of

cat /etc/bash_completion.d/mount

```
andrew@dirkpitt:~$ cat /etc/bash_completion.d/mount
# mount(8) completion. This will pull a list of possible mounts out of
# /etc/{,v}fstab, unless the word being completed contains a ':', which
# would indicate the specification of an NFS server. In that case, we
# query the server for a list of all available exports and complete on
# that instead.
#
have mount &&
{

# Just like COMPREPLY=(`compgen -W "${COMPREPLY[*]}" -- "$cur"`), only better!
#
# This will correctly escape special characters in COMPREPLY.
_reply_compgen_array()
{
    # Create the argument for compgen -W by escaping twice.
    #
    # One round of escape is because we want to reply with escaped arguments. A
    # second round is required because compgen -W will helpfully expand it's
    # argument.
    local i wlist
    for i in ${!COMPREPLY[*]}; do
        local q=$(quote "$(printf %q "${COMPREPLY[$i]}")")
        wlist+=$q$'\n'
    done

    # We also have to add another round of escaping to $cur.
    local ecur="$cur"
    ecur="${ecur//\\/\\\\}"
    ecur="${ecur//\'/\'}"

    # Actually generate completions.
    local oldifs=$IFS
    IFS=$'\n' eval 'COMPREPLY=(`compgen -W "$wlist" -- "${ecur}"`)'
    IFS=$oldifs
}

# Unescape strings in the linux fstab(5) format (with octal escapes).
__linux_fstab_unescape() {
    eval $1="'${!1//\'/\047}'"
    eval $1="'${!1/%\\/\\\\}'"
    eval "$1=$'${!1}'"
}

# Complete linux fstab entries.
#
# Reads a file from stdin in the linux fstab(5) format; as used by /etc/fstab
# and /proc/mounts.
_linux_fstab()
{
    COMPREPLY=()

    # Read and unescape values into COMPREPLY
    local fs_spec fs_file fs_other
    local oldifs="$IFS"
    while read -r fs_spec fs_file fs_other; do
        if [[ $fs_spec = [#]* ]]; then continue; fi
        if [[ $1 == -L ]]; then
            local fs_label=${fs_spec/#LABEL=}
            if [[ $fs_label != "$fs_spec" ]]; then
                __linux_fstab_unescape fs_label
                IFS=$'\0'
                COMPREPLY+=("$fs_label")
                IFS=$oldifs
            fi
        else
            __linux_fstab_unescape fs_spec
            __linux_fstab_unescape fs_file
            IFS=$'\0'
            [[ $fs_spec = */* ]] && COMPREPLY+=("$fs_spec")
            [[ $fs_file = */* ]] && COMPREPLY+=("$fs_file")
            IFS=$oldifs
        fi
    done

    _reply_compgen_array
}

_mount()
{
    local cur sm host prev

    COMPREPLY=()
    _get_comp_words_by_ref -n : cur prev

    case $prev in
        -t|--types)
            _fstypes
            return 0
            ;;
    esac

    [[ "$cur" == \\ ]] && cur="/"

    if [[ "$cur" == *:* ]]; then
        for sm in "$(type -P showmount)" {,/usr}/{,s}bin/showmount; do
            [ -x "$sm" ] || continue
            COMPREPLY=( $( compgen -W "$( "$sm" -e ${cur%%:*} | \
                awk 'NR>1 {print $1}' )" -- "${cur#*:}" ) )
            return 0
        done
    fi

    if [[ "$cur" == //* ]]; then
        host=${cur#//}
        host=${host%%/*}
        if [ -n "$host" ]; then
            COMPREPLY=( $( compgen -P "//$host" -W \
                "$( smbclient -d 0 -NL $host 2>/dev/null |
                sed -ne '/^['"$'\t '"']*Sharename/,/^$/p' |
                sed -ne '3,$s|^[^A-Za-z]*\([^'"$'\t '"']*\).*$|/\1|p' )" \
                    -- "${cur#//$host}" ) )
        fi
    elif [ -r /etc/vfstab ]; then
        # Solaris
        COMPREPLY=( $( compgen -W "$( awk '! /^[ \t]*#/ {if ($3 ~ /\//) print $3}' /etc/vfstab )" -- "$cur" ) )
    elif [ ! -e /etc/fstab ]; then
        # probably Cygwin
        COMPREPLY=( $( compgen -W "$( mount | awk '! /^[ \t]*#/ {if ($3 ~ /\//) print $3}' )" -- "$cur" ) )
    else
        # probably Linux
        if [ "$prev" = -L ]; then
            _linux_fstab -L < /etc/fstab
        elif [ "$prev" = -U ]; then
            COMPREPLY=( $( compgen -W '$(sed -ne "s/^[[:space:]]*UUID=\([^[:space:]]*\).*/\1/p" /etc/fstab )' -- "$cur" ) )
        else
            _linux_fstab < /etc/fstab
        fi
    fi

    return 0
} &&
complete -F _mount -o default -o dirnames mount

# umount(8) completion. This relies on the mount point being the third
# space-delimited field in the output of mount(8)
#
have umount &&
_umount()
{
    local cur
    _get_comp_words_by_ref cur
    COMPREPLY=()

    if [[ $(uname -s) = Linux && -r /proc/mounts ]]; then
        # Linux /proc/mounts is properly quoted. This is important when
        # unmounting usb devices with pretty names.
        _linux_fstab < /proc/mounts
    else
        local IFS=$'\n'
        COMPREPLY=( $( compgen -W '$( mount | cut -d" " -f 3 )' -- "$cur" ) )
    fi

    return 0
} &&
complete -F _umount -o dirnames umount

}

# Local variables:
# mode: shell-script
# sh-basic-offset: 4
# sh-indent-comment: t
# indent-tabs-mode: nil
# End:
# ex: ts=4 sw=4 et filetype=sh
andrew@dirkpitt:~$
```

---

### Post by AndyP79 on 2011-12-30
> **collisionystm said:**
> also post

cat /etc/initramfs-tools/initramfs.conf

```
andrew@dirkpitt:~$ cat /etc/initramfs-tools/initramfs.conf
#
# initramfs.conf
# Configuration file for mkinitramfs(8). See initramfs.conf(5).
#
# Note that configuration options from this file can be overridden
# by config files in the /etc/initramfs-tools/conf.d directory.

#
# MODULES: [ most | netboot | dep | list ]
#
# most - Add most filesystem and all harddrive drivers.
#
# dep - Try and guess which modules to load.
#
# netboot - Add the base modules, network modules, but skip block devices.
#
# list - Only include modules from the 'additional modules' list
#

MODULES=most

#
# BUSYBOX: [ y | n ]
#
# Use busybox if available.
#

BUSYBOX=y

#
# COMPCACHE_SIZE: [ "x K" | "x M" | "x G" | "x %" ]
#
# Amount of RAM to use for RAM-based compressed swap space.
#
# An empty value - compcache isn't used, or added to the initramfs at all.
# An integer and K (e.g. 65536 K) - use a number of kilobytes.
# An integer and M (e.g. 256 M) - use a number of megabytes.
# An integer and G (e.g. 1 G) - use a number of gigabytes.
# An integer and % (e.g. 50 %) - use a percentage of the amount of RAM.
#
# You can optionally install the compcache package to configure this setting
# via debconf and have userspace scripts to load and unload compcache.
# 

COMPCACHE_SIZE=""

#
# COMPRESS: [ gzip | bzip2 | lzma | lzop | xz ]
#

COMPRESS=gzip

#
# NFS Section of the config.
#

#
# BOOT: [ local | nfs ]
#
# local - Boot off of local media (harddrive, USB stick).
#
# nfs - Boot using an NFS drive as the root of the drive.
#

BOOT=local

#
# DEVICE: ...
#
# Specify a specific network interface, like eth0
# Overridden by optional ip= bootarg
#

DEVICE=

#
# NFSROOT: [ auto | HOST:MOUNT ]
#

NFSROOT=auto

andrew@dirkpitt:~$
```

---

### Post by AndyP79 on 2012-01-02
Monday bump

---

### Post by jtarin on 2012-01-02
Are you launching the terminal in a user account or root account? These commands that are listing as not found are normally only accessible under a root account. If you preface each command that was not found with "sudo" it should/would execute.Your first post.....is that what is exhibited in your terminal upon first launch before any command? Character by character?

---

### Post by AndyP79 on 2012-01-02
> **jtarin said:**
> Are you launching the terminal in a user account or root account? These commands that are listing as not found are normally only accessible under a root account. If you preface each command that was not found with "sudo" it should/would execute.Your first post.....is that what is exhibited in your terminal upon first launch before any command? Character by character?

Yes, when I open the terminal that happens first, then I can input whatever I need to no problem. It just started doing it for some reason a while ago, not sure what happened to make it start. So, should I start over on all the help and place sudo in front of each item?

---

### Post by jtarin on 2012-01-02
> **AndyP79 said:**
> Yes, when I open the terminal that happens first, then I can input whatever I need to no problem. It just started doing it for some reason a while ago, not sure what happened to make it start. So, should I start over on all the help and place sudo in front of each item?
No....these programs run in the background without your intervention. Don't be concerned with that. The question is why your user account thinks they need to be run at all from that account.

---

### Post by jtarin on 2012-01-03
Copy and post your .profile file. It can be found as a hidden file in your home folder.

---

### Post by AndyP79 on 2012-01-03
> **jtarin said:**
> Copy and post your .profile file. It can be found as a hidden file in your home folder.

# ~/.profile: executed by the command interpreter for login shells.
# This file is not read by bash(1), if ~/.bash_profile or ~/.bash_login
# exists.
# see /usr/share/doc/bash/examples/startup-files for examples.
# the files are located in the bash-doc package.

# the default umask is set in /etc/profile; for setting the umask
# for ssh logins, install and configure the libpam-umask package.
#umask 022

# if running bash
if [ -n "$BASH_VERSION" ]; then
    # include .bashrc if it exists
    if [ -f "$HOME/.bashrc" ]; then
	. "$HOME/.bashrc"
    fi
fi

# set PATH so it includes user's private bin if it exists
if [ -d "$HOME/bin" ] ; then
    PATH="$HOME/bin:$PATH"
fi

---

### Post by jtarin on 2012-01-03
I'm still having problems with your very first post. When you copied the terminal output your first line was ```
bash: /dev/sda1: Permission denied
```
I would like for you to open a terminal without entering anything and copy the terminal prompt along with the first line.Prompt should be something similar to ```
username@hostname:~$
```

---

### Post by collisionystm on 2012-01-03
the problem is, terminal is automatically issuing the mount command when he opens it

for instance,

if he types 

mount

into terminal and posts the output, we will the same lines in his errors on the OP

---

### Post by collisionystm on 2012-01-03
open terminal, right click on it, go to Profiles, Profile Preferences, Title and command tab

is the box checked for, run custom command instead of my shell

---

### Post by jtarin on 2012-01-03
> **collisionystm said:**
> the problem is, terminal is automatically issuing the mount command when he opens it

for instance,

if he types 

mount

into terminal and posts the output, we will the same lines in his errors on the OPQuite possibly...maybe your on to something. I don't know of anything that would do that except user intervention.:-k

---

### Post by collisionystm on 2012-01-03
> **jtarin said:**
> Quite possibly...maybe your on to something. I don't know of anything that would do that except user intervention.:-k

Yeah I am having a hard time figuring this out. It is always something simple but its hard when your not on the actual machine lol

---

### Post by AndyP79 on 2012-01-03
> **collisionystm said:**
> open terminal, right click on it, go to Profiles, Profile Preferences, Title and command tab

is the box checked for, run custom command instead of my shell

the box marked is update login record when command is launched

---

### Post by AndyP79 on 2012-01-03
> **collisionystm said:**
> Yeah I am having a hard time figuring this out. It is always something simple but its hard when your not on the actual machine lol

Just a quick thanks again for ya'll's help on this. I can image the frustration ya'll have not sitting right here to look at it. Thanks for the patience.

---

### Post by AndyP79 on 2012-01-03
> **jtarin said:**
> I'm still having problems with your very first post. When you copied the terminal output your first line was ```
bash: /dev/sda1: Permission denied
```
I would like for you to open a terminal without entering anything and copy the terminal prompt along with the first line.Prompt should be something similar to ```
username@hostname:~$
```

It does not have the promt, it just starts out exactly as that first post. :confused:

---

### Post by collisionystm on 2012-01-04
just got sh*ts and giggles can you post the output of 

cat /etc/fstab

and then

open a new terminal, once that output is finished

type 

bash

do you get the same output again?

---

### Post by AndyP79 on 2012-01-06
> **collisionystm said:**
> just got sh*ts and giggles can you post the output of 

cat /etc/fstab

and then

open a new terminal, once that output is finished

type 

bash

do you get the same output again?


Sorry about the delay, thought I posted to this, guess I forgot to hit submit. Here is the results

andrew@dirkpitt:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=043c8892-cb4a-4b5d-aa1a-bdec7a74c5fc /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=ef1fceaa-ba11-472f-9112-8df62205f36d none            swap    sw              0       0
andrew@dirkpitt:~$ 


andrew@dirkpitt:~$ bash
bash: /dev/sda1: Permission denied
No command 'proc' found, did you mean:
 Command 'nproc' from package 'coreutils' (main)
 Command 'proj' from package 'proj-bin' (universe)
proc: command not found
sysfs: command not found
fusectl: command not found
No command 'none' found, did you mean:
 Command 'nona' from package 'hugin-tools' (universe)
 Command 'one' from package 'opennebula' (universe)
 Command 'note' from package 'note' (universe)
 Command 'cone' from package 'cone' (universe)
 Command 'node' from package 'node' (universe)
 Command 'node' from package 'nodejs' (universe)
none: command not found
No command 'none' found, did you mean:
 Command 'nona' from package 'hugin-tools' (universe)
 Command 'one' from package 'opennebula' (universe)
 Command 'note' from package 'note' (universe)
 Command 'cone' from package 'cone' (universe)
 Command 'node' from package 'node' (universe)
 Command 'node' from package 'nodejs' (universe)
none: command not found
No command 'udev' found, did you mean:
 Command 'udv' from package 'ncbi-tools-x11' (universe)
 Command 'udav' from package 'udav' (universe)
 Command 'udevd' from package 'udev' (main)
udev: command not found
devpts: command not found
No command 'tmpfs' found, did you mean:
 Command 'mtpfs' from package 'mtpfs' (universe)
tmpfs: command not found
No command 'none' found, did you mean:
 Command 'nona' from package 'hugin-tools' (universe)
 Command 'one' from package 'opennebula' (universe)
 Command 'note' from package 'note' (universe)
 Command 'cone' from package 'cone' (universe)
 Command 'node' from package 'node' (universe)
 Command 'node' from package 'nodejs' (universe)
none: command not found
No command 'none' found, did you mean:
 Command 'nona' from package 'hugin-tools' (universe)
 Command 'one' from package 'opennebula' (universe)
 Command 'note' from package 'note' (universe)
 Command 'cone' from package 'cone' (universe)
 Command 'node' from package 'node' (universe)
 Command 'node' from package 'nodejs' (universe)
none: command not found
binfmt_misc: command not found
gvfs-fuse-daemon: command not found
bash: .: /etc/bash_completion.d/iftop: cannot execute binary file
andrew@dirkpitt:~$ 


Still the same afterwards:(

---

### Post by collisionystm on 2012-01-06
btw... I noticed the Dirk Pitt. 

Cussler Rocks!

---

### Post by AndyP79 on 2012-01-07
> **collisionystm said:**
> btw... I noticed the Dirk Pitt. 

Cussler Rocks!

I have to admitt I am a little behind. I have 3 unread books sitting on the shelf, and I think I need to pick up the last 3. I have almost all of his books in hardback.

---

### Post by collisionystm on 2012-01-07
> **AndyP79 said:**
> I have to admitt I am a little behind. I have 3 unread books sitting on the shelf, and I think I need to pick up the last 3. I have almost all of his books in hardback.

My favorite author to read on a plane ride. Keeps me occupied.

---

### Post by AndyP79 on 2012-01-10
Tuesday afternoon bump

---

### Post by georgemc on 2012-01-10
This is what I would do at this stage.

I would attempt to isolate the area in .bashrc that is causing these issues.

I would "bracket" one statement block at a time with "set -x" and "set +x" to find where all of this is coming from.  The "set -x" switches debug output on and the "set +x" switches it off.

For example:
```

# ~/.bashrc: executed by bash(1) for non-login shells.
# see /usr/share/doc/bash/examples/startup-files (in the package bash-doc)
# for examples

#if [ "$PS1" ] ; then  
#   mkdir -m 0700 /dev/cgroup/cpu/user/$$
#   mkdir -p -m 0700 /dev/cgroup/cpu/user/$$  > /dev/null 2>&1
#   echo $$ > /dev/cgroup/cpu/user/$$/tasks
#  echo "1" > /dev/cgroup/cpu/user/$$/notify_on_release
#fi

# If not running interactively, don't do anything
[ -z "$PS1" ] && return
[COLOR=Red]set -x[/COLOR]
# don't put duplicate lines in the history. See bash(1) for more options
# ... or force ignoredups and ignorespace
HISTCONTROL=ignoredups:ignorespace
[COLOR=Red]set +x[/COLOR]
# append to the history file, don't overwrite it
shopt -s histappend
........
........

```In the  example above I bracketed the HISTCONTROL statement block with "set -x" and "set +x"; saved .bashrc; then I opened a terminal or typed in "bash" into a terminal.  You will see something like the following.

```

user@ubuntu-desktop:~/$ bash
+ HISTCONTROL=ignoredups:ignorespace
+ set +x
user@ubuntu-desktop:~/$ 

```Now rinse and repeat for every statement block through out .bashrc until you find the block that produces some thing like this:

```

user@ubuntu-desktop:~/$ bash
+ SOME .BASHRC STATEMENT STUFF
[COLOR=Red]bash: /dev/sda1: Permission denied   [COLOR=Black]<< the issue output[/COLOR]
No command 'proc' found, did you mean:
.... and all the rest ....[/COLOR]
+ SOME MORE .BASHRC STATEMENT STUFF
user@ubuntu-desktop:~/$ bash

```This may narrow it down to a specific part, program, shell script etc.

This will take some time to edit .bashrc, then invoke bash, compare the output, move the "set -+x" bracket to the next block.

See if you can narrow it down to some thing more specific.  When you narrowed it down please post the beginning of the output so we can figure out where to go next.

Hope this helps.

George

---

