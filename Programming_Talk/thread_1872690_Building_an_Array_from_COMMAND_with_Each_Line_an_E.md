---
title: "Building an Array from COMMAND with Each Line an Element"
date: 2011-10-31
forum: Programming Talk
---

### Post by jamesisin on 2011-10-31
I have written a few scripts now where I wanted to take the output of some command and direct that into an array where each line of output from the command was a separate element in the array.  I have not found a satisfactory way of doing this.  Most recently I have tried this method:

```
playlistopen=`sed -n '/'"$thisplaylist"'/=' "$rhythmboxlists"` #this gives the line number for the specified list opening tag

echo
echo $playlistopen
echo

declare -a playlistlines

playlistlinesfunction ()
   {
      local IFS
      IFS=\n
      playlistlines=`sed -n "$playlistopen"',/<\/playlist>/=' "$rhythmboxlists"` #this gives ALL line numbers from 14 to the closing tag
      echo "In the function."
      echo $playlistlines
      count=${#playlistlines[@]}
      echo "There are "$count "elements."
   }

playlistlinesfunction

echo
count=${#playlistlines[@]}
echo "There are "$count "elements."
echo "Outside the function."
echo $playlistlines
echo

exit
```

This gives me an array with one element.  The IFS does change yet this only effects the output display of the array in the terminal and not the output of *sed* as the array is built.

In the past I have used this admittedly sloppy solution:

```
# parse files into array recursively
 
find "$directory" -type f -name '*.[Ff][Ll][Aa][Cc]' > /tmp/whyme

declare -a flacfind
   let i=0
   while read flacline; do
      flacfind[$i]=$flacline
      ((i++))
   done < /tmp/whyme

# use array to build OggS command

for (( i=0 ; i < ${#flacfind[@]} ; i++ )) ; do
   echo "I am attempting to set OggS for ${#flacfind[@]} files."
   OggS\ Set.app/Contents/MacOS/Set\ OggS "${flacfind[i]}" ; 
   done 
```

If I direct the output from *find* into a file and use that file as input for the array I get my element per command output as desired.

Surely there is a more elegant manner in which to get this done?

---

### Post by sisco311 on 2011-10-31
BASH 4
```
mapfile -t array < file
mapfile -t array < <(find ./ -iname '*.flac' -type f)

```

BASH  (>= 3.1)
```
while IFS= read -r -d ''
do
    array+=("$REPLY")
done< <(find ./ -iname '*.flac' -type f -print0)

```

For details see BashFAQ 005.

---

