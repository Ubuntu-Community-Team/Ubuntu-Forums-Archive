---
title: "Python improvement sortfile by extension and size"
date: 2011-06-16
forum: Programming Talk
---

### Post by jao_madn on 2011-06-16
Hi i had this python script to sort source dir by file extension and cp to individual extension destination dir. i would like to ask in addition to file extension sorting an option for size sorting somewhat like

# <script.py> -size <range 10k-20k>,<range 30k-40k>,..... source destination

Im a beginner and doing my homeworks for this one. Hope someone can add to the scripts.

Thanks for any responce in advance.

```

import os
import os.path
import shutil
import sys

source = sys.argv[1]
destination = sys.argv[2]

while not os.path.exists(source):
    source = raw_input('Enter a valid source directory\n')
while not os.path.exists(destination):
    destination = raw_input('Enter a valid destination directory\n')

for root, dirs, files in os.walk(source, topdown=False):
    for file in files:
        extension = os.path.splitext(file)[1][1:].upper()
    destinationPath = os.path.join(destination,extension)
      
    if not os.path.exists(destinationPath):
            os.mkdir(destinationPath)
    if os.path.exists(os.path.join(destinationPath,file)):
            print 'WARNING: this file was not copied :' + os.path.join(root,file)
    else:
        shutil.copy2(os.path.join(root,file), destinationPath)

```

---

### Post by Tony Flury on 2011-06-16
Is this homework - in which case we will not write code for you - what would you learn if all we did is do your work for you. In the worst case your tutor could note that you are not doing your own work, and reject it (or you).

You will learn if you try to write the code yourself - and get stuck - and then you can come back and ask something specific about the code you have used.

I will give you a hint though : There are standard libraries available in python to do command line argument/option parsing - it might be worth looking at them before going any further. I think there is also libraries available to get useful information about files (including sizes, permissions etc.

---

### Post by jao_madn on 2011-06-16
Thanks for the comments..

Just wondering for any available help and understanding in obtaining my objective.

Im in the process of understanding python right now but its urgent needed for my foremost data recovery file sorting. I looking onward on using os.path.getsize() right now but as i said im kind of getting my foremost done. By the way thanks for the hint.

---

