---
title: "BASH script recursion for shnsplit"
date: 2010-03-03
forum: Programming Talk
---

### Post by jamesisin on 2010-03-03
I am writing a script to convert album APE files into track FLAC files recursively in a folder hierarchy.  At first I tried this:

```
# split album APE into track FLAC files
# assumes all .ape and .cue files are named a
# recursive

printf "%b\n\n" "I will need to know from which directory to recurse.\n"
read -p "Give the path to the root of the problem: "

for filelist in "${REPLY[@]}"; do
   find

aflac=()
   for albumflac in "${filelist[@]}"; do
      read -r 
   done << grep a.flac

acue=()
   for albumcue in "${filelist[@]}"; do
      read -r
   done << grep a.cue

shnsplit -o flac -f "${albumcue[@]}" -t "%n - %t" "${albumflac[@]}"

done
```

This gave me errors, so I used this instead:

```
# split album APE into track FLAC files
# assumes all .ape and .cue files are named a
# recursive

printf "%b\n\n" "I will need to know from which directory to recurse.\n"
read -p "Give the path to the root of the problem: "

for filelist in "${REPLY[@]}"; do
   find

aflac=()
   for albumflac in "${filelist[@]}"; do
      grep a.flac
   done

acue=()
   for albumcue in "${filelist[@]}"; do
      grep a.cue
   done

shnsplit -o flac -f "${albumcue[@]}" -t "%n - %t" "${albumflac[@]}"

done
```

This gave no errors but did no useful work and hung after the find listed its files.

Oh, and find runs recursive from the pwd and not the $REPLY directory.

Am I close?

---

### Post by jamesisin on 2010-03-03
I fixed the pwd v $REPLY problem.  Here is the current version (which still hangs after showing the find results):

```
# split album APE into track FLAC files
# assumes all .ape and .cue files are named a
# recursive

printf "%b\n"
printf "%b\n" "I will need to know from which directory to recurse.\n"
read -p "Give the path to the root of the problem: "

for filelist in "${REPLY[@]}"; do
   find "${REPLY[@]}"
done

aflac=()
   for albumflac in "${filelist[@]}"; do
      grep a.flac
   done

acue=()
   for albumcue in "${filelist[@]}"; do
      grep a.cue
   done

shnsplit -o flac -f "${albumcue[@]}" -t "%n - %t" "${albumflac[@]}"

done
```

---

### Post by jamesisin on 2010-03-03
Ok, so this works:

```
playlists=()
while IFS='"' read -r _ playlist _; do 
  playlists+=( "$playlist" )
done < <(grep '<playlist name=.*type="static"' "$rhythmboxlists")
```

but this does not:

```
splitlist=()
while IFS="" echo oops; do
   for filelist in "${REPLY[@]}"; do
      find "${filelist[@]}"
      splitlist+=( "$filelist" )
      echo 2
   done
   echo 3
done
```

The first is from a script I am writing to synk some playlists.  It adds individual entries to the playlists array.

The second is what I'm working on for this shnsplit script.  It yields an infinite loop (or one long enough for me to interrupt it), printing the three echoes and the find results.  I just want it to add a list of available files and folders under the (aforementioned) recursive root folder to the splitlist array.

I don't know what I'm doing wrong.

---

### Post by jamesisin on 2010-10-05
I have completed and published this script:

[http://www.soundunreason.com/InkWell/?p=2485](http://www.soundunreason.com/InkWell/?p=2485)

---

