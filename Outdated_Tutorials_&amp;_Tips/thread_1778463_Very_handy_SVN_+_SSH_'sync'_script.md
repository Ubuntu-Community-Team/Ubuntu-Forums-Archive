---
title: "Very handy SVN + SSH 'sync' script"
date: 2011-06-09
forum: Outdated Tutorials &amp; Tips
---

### Post by Kungen7 on 2011-06-09
This is a script i practically use all the time. I think its kind of genius, do you? Please give feedback and critique! :pinguin:
(You might find this post else where on the web, but without response)

Here is my scenario:
I have a workstation at home and a laptop for school. I also have headless server, made from an historical HP Pavilion workstation. 
Since i use my laptop every day at school, i need to get my projects over to my workstation so i can keep on working when i come home. Thats where my server comes in. I just run 'sync' on my laptop and it updates the project through svn repositories at the server. I can then sync the workstation and VIOLA!

```
#!/bin/bash

# SVN synchronize script
# By 7SLEVIN


# Response
. getYn
prompt='Commit before checkout?(y/n) '

# Vars
commitall=false
all=false

bin=( false "bin" )
docs=( false "Documents" )
it=( false "IT" )
log=( false "Log" )
pics=( false "Pictures" )

reps=( bin docs it log pics )

# Set host
if [[ $(hostname) == "gordias" ]]; then
  URL="file:///home/svn"
  echo URL=$URL
else
  URL="svn+ssh://xxx.xxx.xx.xxx/home/svn"
  echo URL=$URL
fi

# Getopts
while getopts cbdilp opt; do
  case "$opt" in
    c) commitall=true;;
    b) bin[0]=true;;
    d) docs[0]=true;;
    i) it[0]=true;;
    l) log[0]=true;;
    p) pics[0]=true;;
    *) continue;;
  esac
done
shift $[ $OPTIND -1 ]

count=1
for param in "$@"; do
  if [[ $param == "all" ]]; then
    all=true
  fi
  count=$[ $count + 1]
done


# MAIN
cd /home/$USER

count=0
for rep in ${reps[@]}; do
  temp="\${$rep[*]}"
  rep=`eval echo $temp`
  
  # Assigning variables from array
  count2=0
  for var in $rep; do
    if [[ $count2 == 0 ]]; then
      bool=$var
    elif [[ $count2 == 1 ]]; then
      dir=$var
    fi
    count2=$[ $count2 + 1 ]
  done

  # Check if rep is true, if not exit
  if ! $all; then
    if ! $bool; then
      continue
    fi
  fi
  
  echo ""
  
  # SVN
  output=`svn status $dir`
  # if output is blank then there is no changes
  if [[ $output == "" ]]; then
    echo "$dir: unchanged"
    svn co $URL/$dir
  # if not, commit before checkout
  else
    echo "$dir:"
    echo $output 
    # Commmit
    if $commitall; then
      svn commit $dir/ -m 'Commited by sync'
    else
      if $(getYn "$prompt"); then
      svn commit $dir/ -m "Commited by sync"
      fi
    fi
    svn co $URL/$dir
  fi

  count=$[ $count + 1 ]
done

exit 0
```

Run by:
```

sync all
sync -c all
sync -bdp

```

Ive made the code generic so you dont have to make a lot of changes if you what to add/remove a repository. 
You can also run the script on the server, though this is not thoroughly testet. See # Set host.
To use the keyless SSH implementation see links at bottom. (Its awesome...)

Other remarks:[LIST]
[*]You can sync all repositories with the 'all' option.
[*]You can commit all and skip the prompt with the '-c' option.
[*]It features getopts for easy option handling.
[*]It features SSH for safe data transfers.
[/LIST]

The getYn file is included below.
```
#!/bin/bash

# Function get yes or no with custom prompt
# By 7SLEVIN

getYn ()
{
prompt="$1"
while true
do
	read -p "$prompt" yn
	case $yn in
		[Yy]* ) ans=true;break;;
		[Nn]* ) ans=false;break;;
		* ) ;;
	esac
done
echo $ans
}
```



Thanks to lunda for post on multidimensional arrays!
[BASH: multidimensional array - lunda's posterous](http://lunda.posterous.com/bash-multidimensional-array)

My links on SVN and SSH:
[https://help.ubuntu.com/community/Subversion](https://help.ubuntu.com/community/Subversion)
[SSH Tutorial for Linux - Support Documentation](http://support.suso.com/supki/SSH_Tutorial_for_Linux#Generating_a_key)

---

### Post by _stella_ on 2011-06-30
Thank, i'll try the script.

---

