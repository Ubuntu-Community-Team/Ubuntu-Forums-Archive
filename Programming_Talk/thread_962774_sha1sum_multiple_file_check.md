---
title: "sha1sum multiple file check"
date: 2008-10-29
forum: Programming Talk
---

### Post by altonbr on 2008-10-29
I'm looking to compare one file on my server against multiple of the same name using sha1sum.

This is all I have so far, but I'm stuck where I need to check the seed sha1sum against multiple other files of the same name.
```
#!/bin/bash

# file to check against
SEED_DIR='/dir/example/'
# file to check
FILE='file.txt'

# sha1 hash of the seed file
SHA1=`sha1sum $SEED_DIR$FILE > seed.sha1`

# find all files on the server that have the same name as the seed
FILES=`find / -iname $FILE`

# TODO:
# This is where I am lost. How do I check the one sha1sum against all the files I just found using 'find'?
#sha1sum --check seed.sha1
```

Thanks for your help!

---

### Post by stylishpants on 2008-10-29
Here's one way:

```
#!/bin/bash

set -e

# Print the given file's sha1, strip off the filename 
get_sha1()
{
	sha1sum "${1}" | awk '{print $1}'
}

# file to check against
SEED_DIR='/example/dir/'

# file to check
FILE='file.txt'

TARGET_SHA1=`get_sha1 "${SEED_DIR}/${FILE}"`

echo "target is ${TARGET_SHA1}"

find / -type f -name "${FILE}" | \
while read f
do
	the_sha1=`get_sha1 "${f}"`

	if [ "${the_sha1}" = "${TARGET_SHA1}" ]
	then
		echo "Found match: '${f}'"

		# uncomment this to stop on the first match
#		break
	fi

done

```

---

### Post by ghostdog74 on 2008-10-29
```

# file to check against
SEED_DIR='/home/yhlee/test'
FILE='file'
set -- $(sha1sum "${SEED_DIR}/${FILE}")
TARGET_SHA1=$1
find . -type f |xargs -i sha1sum "{}" |grep "$TARGET_SHA1" >/dev/null && echo "found"




```

---

