---
title: "TIP - Record all edits to system files"
date: 2011-07-28
forum: Outdated Tutorials &amp; Tips
---

### Post by wolterh on 2011-07-28
Have you ever wondered how to easily record the changes you make to system files without taken much time from yourself?

I did, and I have written a small bash script that I think is the solution to this problem. 

I have called it **logedit**, and here is the source for it:

```

# LOGEDIT
# Log your edits to any text file. Created to log edits of system files.
# Author: Wolter Hellmund <wolterh6@gmail.com>
# License: CC-BY-SA v3.0
# Created 2011-07-27
#
# Usage: 
#  logedit FILE
#
# Hierarchy
#  YYYY-mm-dd-HHMM.path.to.file.ext#pre-edit
#  YYYY-mm-dd-HHMM.path.to.file.ext#user-comment

file="${1}"

logdir="${HOME}/.local/share/logedit/"
if [ ! -d $logdir ]; then
	mkdir -p "${logdir}";
fi;

function log {
	splitname=`readlink -f $1`
	splitname=${splitname//\//.}
	splitname=${splitname:1}
	lastlogged=`date +%Y"-"%m"-"%d"-"%H%M"-"%S`"-""${splitname}#${2}"
	cp "${1}" "${logdir}"/"${lastlogged}"
}

# Execute
log "${file}" "pre-edit"
# Edit
sensible-editor "${file}"
# Ask for comment
echo "Please enter a short comment to identify your edit:"
read postedit
# Save modified copy, with comment
log "${file}" "${postedit}"

```

I hope you find this useful! I am no experienced bash script coder, so if you find any errors or think you could improve the script in any way, feel ever so free to comment about it.

---

