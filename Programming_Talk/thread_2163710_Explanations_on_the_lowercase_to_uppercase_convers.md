---
title: "Explanations on the lowercase to uppercase conversion script please"
date: 2013-07-19
forum: Programming Talk
---

### Post by bkpsusmitaa on 2013-07-19
I have the script from advanced bash scripting guide. There are some things which I could not understand.
==============================================
```
#!/bin/bash
# upperconv.sh
# Converts a specified input file to uppercase.

E_FILE_ACCESS=70 
E_WRONG_ARGS=71

# query ## why these two are introduced here? if these exit codes
#+ are required where are they required?

if [ ! -r "$1" ]     # Is specified input file readable?
then
  echo "Can't read from input file!"
  echo "Usage: $0 input-file output-file"

# query # how these patterns are grabbed using $0, $1and $2? Are these codes in-built?

  exit $E_FILE_ACCESS   # # query #how these outputs are used, and where? what is its significance?
fi                   #  Will exit with same error
                     #+ even if input file ($1) not specified (why?).

if [ -z "$2" ]
then
  echo "Need to specify output file."
  echo "Usage: $0 input-file output-file"
  exit $E_WRONG_ARGS    # query #how these outputs are used, and where? Significance?
fi


exec 4<&0
exec < $1            # Will read from input file.

exec 7>&1
exec > $2            # Will write to output file.
                     # Assumes output file writable (add check?).
## query ### Can't write if output file is readonly.
# -----------------------------------------------
    cat - | tr a-z A-Z   # Uppercase conversion.
#   ^^^^^                # Reads from stdin.
#           ^^^^^^^^^^   # Writes to stdout.
# However, both stdin and stdout were redirected.
# Note that the 'cat' can be omitted.
# -----------------------------------------------

exec 1>&7 7>&-       # Restore stout.
exec 0<&4 4<&-       # Restore stdin.

# After restoration, the following line prints to stdout as expected.
echo "File \"$1\" written to \"$2\" as uppercase conversion."

exit 0
```

---

### Post by Vaphell on 2013-07-19
wrap the code in ```
 [/co****de] tags, it's unreadable

conversion itself is craptastic, works only with base a-z chars and not with diactric heavy language specific versions

[code]sed 's/.*/\U&/' input_file
```
bash can turn variable all-caps with *${variable^^}*

and why you are reading advanced bash stuff if you don't know what $0, $1 and $2 are and what *exit* does? That's Bash 101 material.

$0 script itself
$1, $2 actual params (input file, output file)
if input file unreadable exit script with error code 70
if output missing/bad parameters exit script with error code 71
exit codes are used outside the script in case you want to recognize how it failed so you can program around it or whatever

---

### Post by bkpsusmitaa on 2013-07-19
> **Vaphell said:**
> ...why you are reading advanced bash stuff if you don't know what $0, $1 and $2 are and what *exit* does?...
$0 script itself
$1, $2 actual params (input file, output file)...
Baptism by fire... :) I know the definitions, they're in the file. I wanted to know if this is inbuilt? If so, it would provide me an opportunity to go through the source code to see how it's done. 

> **Vaphell said:**
> ...if input file unreadable exit script with error code 70
if output missing/bad parameters exit script with error code 71
exit codes are used outside the script in case you want to recognize how it failed so you can program around it or whatever
I know, but where are these exit codes used in this particular code?

And why to invoke sed from within bash? It is not intrinsic to bash.

---

### Post by Vaphell on 2013-07-19
> Baptism by fire...

more like monumental waste of time looking at things way beyond comprehension

> I know the definitions, they're in the file. I wanted to know if this is inbuilt? If so, it would provide me an opportunity to go through the source code to see how it's done. 

The thing is it's obvious what they are even without comments, because as i said it's bash 101
positional parameters are always $(number) or written differently ${(number)}

you run this
```
$ ./script some-param 'some other' param and another one
      $0       $1           $2      $3   $4    $5    $6  <- these will be usable inside the script
```

> I know, but where are these exit codes used in this particular code?
They are defined and used to quit the script prematurely while signaling the type of failure to the outside world and that's it because that's all that can be done. You don't anything else with exit codes inside the script because that can only happen when the script EXITS and ceases to exist.

```
./script.sh param1 param2
exitcode=$?

if (( exitcode=0 )); then
  echo "Everything went fine"
elif (( exitcode=70 )); then
  echo "Error: input file was unreadable"
elif (( exitcode=71 )); then 
  echo "Error: bad parameters"
else
  echo "Error: unknown error"
fi
```

> And why to invoke sed from within bash? It is not intrinsic to bash. 
And this is different from invoking **tr**, which is what is done in the script, how? Feature intristic to bash would be using **${variable^^}** where variable stores the text
```
while read -r ln; do echo "${ln^^}"; done < input_file > output_file
```

---

### Post by bkpsusmitaa on 2013-07-19
> monumental waste of time looking at things way beyond comprehension
... like a child learning to speak, like a child...
Not if I have compatriots and OSS enthusiasts like you! Thank you

---

