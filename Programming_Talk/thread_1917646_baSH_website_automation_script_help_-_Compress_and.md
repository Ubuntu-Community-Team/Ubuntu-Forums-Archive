---
title: "baSH website automation script help - Compress and archive"
date: 2012-01-30
forum: Programming Talk
---

### Post by sikuneh on 2012-01-30
I am writing a website and I want to automate the process of compressing and archiving the current Release folder, moving it into the Legacy folder, then moving the contents of the Dev folder into Release. I don't understand tar and gzip very well so I would like some help with the compressing and archiving part.

Here is what I have so far:
```

#!/bin/bash

NOW=$(date +"%m-%d-%y")

# Change to the Reviews directory
cd /opt/lampp/htdocs/Reviews/

# First compress the contents of the current Release folder called Release.mm-dd-yy

# Compress and archive release folder here

# Move the compressed archive to ./Legacy
mv -r "./Release.$NOW.tar.gz" ./Legacy

# Clear the folder for the new files
cd Release
rm -r *
cd ../

mv -r ./Dev/* ./Release

echo "Completed successfully.\n"

```

---

