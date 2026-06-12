---
title: "&quot;Compile&quot; script with command line"
date: 2013-04-13
forum: Programming Talk
---

### Post by pedrommone on 2013-04-13
I have a bash script like this one

```

#!/bin/bash

SERVER_ID=1
SERVER_NAME="Brazil-1"
SERVER_IP="123.213.123.123"
SERVER_TYPE="Privado"

// do stuff
```

I want to run other script called make-config.sh, it should "compile" the first script variables (set them) like this command 

```
make-config.sh -server_id 123 server_name "name" server_ip = "123.123.123.123" server_type = "private"
```

The problem is that I have no idea of how do it, someone can share some tutorials about that? Thanks.

---

### Post by r-senior on 2013-04-13
Do you need to use long options, i.e. "make-config --serverid=xyz" or would short options suffice, e.g. "make-config -s xyz"?

---

### Post by schragge on 2013-04-13
You can use [getopt]("http://manpages.ubuntu.com/manpages/precise/en/man1/getopt.1.html") and a [here-document](http://www.gnu.org/software/bash/manual/html_node/Redirections.html#Here-Documents) for it
```

cat <<END >~/compiled-script.bash
#!/bin/bash

SERVER_ID=$server_id
SERVER_NAME=$server_name
SERVER_IP=$server_ip
SERVER_TYPE=$server_type
END

```

---

### Post by pedrommone on 2013-04-13
> **r-senior said:**
> Do you need to use long options, i.e. "make-config --serverid=xyz" or would short options suffice, e.g. "make-config -s xyz"?

Doesnt matter they size, I just want know how to do it.

> **schragge said:**
> You can use [getopt]("http://manpages.ubuntu.com/manpages/precise/en/man1/getopt.1.html") and a [here-document]("http://www.gnu.org/software/bash/manual/html_node/Redirections.html#Here-Documents") for it
```

cat <<END >~/compiled-script.bash
#!/bin/bash

SERVER_ID=$server_id
SERVER_NAME=$server_name
SERVER_IP=$server_ip
SERVER_TYPE=$server_type
END

```

For real, didnt get how to use it.

---

### Post by r-senior on 2013-04-13
If short options are OK, you can use the Bash getopts builtin:

[http://wiki.bash-hackers.org/howto/getopts_tutorial](http://wiki.bash-hackers.org/howto/getopts_tutorial)

If you need long options, you can use the getopt program, as suggested by schragge. Here's an example: [http://software.frodo.looijaard.name/getopt/docs/getopt-parse.bash](http://software.frodo.looijaard.name/getopt/docs/getopt-parse.bash)

I haven't checked that either of these examples work.

---

### Post by pedrommone on 2013-04-13
> **r-senior said:**
> If short options are OK, you can use the Bash getopts builtin:

[http://wiki.bash-hackers.org/howto/getopts_tutorial](http://wiki.bash-hackers.org/howto/getopts_tutorial)

If you need long options, you can use the getopt program, as suggested by schragge. Here's an example: [http://software.frodo.looijaard.name/getopt/docs/getopt-parse.bash](http://software.frodo.looijaard.name/getopt/docs/getopt-parse.bash)

I haven't checked that either of these examples work.

But, how to save them into compiled-bash.sh?

---

### Post by steeldriver on 2013-04-13
You could have your getopt script create a file that exports the variables, and then *source* it from your other script, e.g.

```
$ server_id=1; server_type="Privado"
$ 
$ cat > servervars <<EOF
export SERVER_ID="$server_id"
export SERVER_TYPE="$server_type"
EOF
$ 
$ echo $SERVER_ID $SERVER_TYPE

$ 
$ source servervars
$ echo $SERVER_ID $SERVER_TYPE
1 Privado
$ 
```

FWIW you should probably avoid using ALL_CAPS names though as these are traditionally reserved for system variables

---

### Post by schragge on 2013-04-13
This is just a minimal example. Better check the manual page of getopt and study the example script linked by **r-senior** above to understand how getopt works.
```

script="compiled-bash.sh"
temp=`getopt -l id:,name:,address:,type: -n "$0" -- '' "$@"` || exit 1
eval set -- optname optval "$temp"
declare -A opt
while shift 2; do
  case $1 in
    --id|--name|--address|--type) opt[${1#--}]="$2";;
  esac
done
cat <<EOF >"$script"
#!/bin/bash

SERVER_ID=${opt[id]}
SERVER_NAME=${opt[name]}
SERVER_IP=${opt[address]}
SERVER_TYPE=${opt[type]}
EOF

```

---

### Post by pedrommone on 2013-04-13
> **schragge said:**
> This is just a minimal example. Better check the manual page of getopt and study the example script linked by **r-senior** above to understand how getopt works.
```

script="compiled-bash.sh"
temp=`getopt -l id:,name:,address:,type: -n "$script" -- '' "$@"` || exit 1
eval set -- optname optval "$temp"
declare -A opt
while shift 2; do
  case $1 in
    --id|--name|--address|--type) opt[${1#--}]="$2";;
  esac
done
cat <<EOF >"$script"
#!/bin/bash

SERVER_ID=${opt[id]}
SERVER_NAME=${opt[name]}
SERVER_IP=${opt[address]}
SERVER_TYPE=${opt[type]}
EOF

```

I should call it using compiler.sh --id or --name? If the script already exists, it will override it?

---

### Post by schragge on 2013-04-13
Yep. E.g. ```
./compiler.sh --id=1 --name 'Brazil-1' --address 1.2.3.4 --type="Privado"
```

---

### Post by pedrommone on 2013-04-13
> **schragge said:**
> Yep. E.g. ```
./compiler.sh --id=1 --name 'Brazil-1' --address 1.2.3.4 --type="Privado"
```

It will override if already exists?

---

### Post by schragge on 2013-04-13
Yes, it will overwrite the old file contents unless you put *set -C* or *set -o noclobber* before it.

---

### Post by pedrommone on 2013-04-13
Ok, thanks buddy!

---

### Post by pedrommone on 2013-04-13
It is giving one error

> compile-tunnel.sh: 5: compile-tunnel.sh: declare: not found

---

### Post by schragge on 2013-04-13
Well, *declare* is a bash-specific builtin. Is compile-tunnel.sh a */bin/sh* script? Then you cannot use associative arrays in it.

---

### Post by pedrommone on 2013-04-13
No, is bash script

---

### Post by schragge on 2013-04-13
Then you either source it from a */bin/sh* script or invoke it with *sh compile-tunnel.sh* The error message you get is not from bash, it's from dash.

---

### Post by r-senior on 2013-04-14
> **schragge said:**
> The error message you get is not from bash, it's from dash.
@pedrommone: It's quite common on Debian-based systems for people to write scripts with this shebang line at the top:

```
#!/bin/sh
```

or launch them with [FONT=Courier New]/bin/sh[/FONT] and still believe they are running a Bash script because Bash is the default shell used by the terminal ([FONT=Courier New]/bin/bash[/FONT] is the shell added to [FONT=Courier New]/etc/passwd[/FONT] by default when a new user is created). But if you look at [FONT=Courier New]/bin/sh[/FONT] on a Debian-based system, including Ubuntu, you'll see that [FONT=Courier New]/bin/sh[/FONT] is linked to [FONT=Courier New]/bin/dash[/FONT], which is the ["(D)ebian (A)lmquist (Sh)ell]("https://en.wikipedia.org/wiki/Debian_Almquist_shell).

```
$ ls -l /bin/sh
lrwxrwxrwx 1 root root 4 Mar 29  2012 /bin/sh -> dash
```

So you need to take care to ensure you are invoking a Bash script if you intend to use Bash-specifics, e.g.:

```
#!/bin/bash
```

---

### Post by pedrommone on 2013-04-14
I was using sh when callling the script, now I dont 'compile' mysql commands like this one

```
USER_TIME=$(mysql -u $DB_USER -p$DB_PASS -h$DB_HOST $DB_NAME --disable-column-names -e "SELECT TIME_TO_SEC(TIMEDIFF(now(), online_users.updated_at)) FROM online_users WHERE user_id = $USER_ID ORDER BY updated_at ASC")
```

It execute them when I ran compile-tunnel.sh

---

### Post by pedrommone on 2013-04-16
How I can put my whole bash inside a 'string'? Cat is executing the script, I just want 'compile' it!

---

