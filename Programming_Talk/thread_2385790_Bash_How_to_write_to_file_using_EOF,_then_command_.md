---
title: "Bash: How to write to file using EOF, then command afterwards?"
date: 2018-02-25
forum: Programming Talk
---

### Post by peppy3 on 2018-02-25
Greetings,

I'm trying to create a bash script that adds a config file to Apache, and then after the file is written, use a command to enable the config file in apache, and then reload apache:

```

#!/bin/bash

FILE="/etc/apache2/sites-available/mysite.com.conf"

/bin/cat <<EOF > $FILE
<VirtualHost *:80>
   stuff ....
</VirtualHost>
EOF

sudo a2ensite mysite.com.conf && sudo systemctl reload apache2

```

However, this is not working. It writes and saves the file, but the bottom part of the script gets written into the file as text, this part:

```

EOF

sudo a2ensite mysite.com.conf && sudo systemctl reload apache2
```

Trying to enable the site or reload apache causes an error because of this extra stuff getting written in when it's not supposed to.

How do I write a script like this, such as writing the config details to a file and then two commands after the file is created. Commands must run one after the other.

Thanks
Kind regards

---

### Post by steeldriver on 2018-02-25
That shouldn't happen - is the example you gave exact and verbatim (no additional indentation for example)? Have you checked for non-printable characters e.g. by displaying your script with `cat -et`?

---

### Post by peppy3 on 2018-02-25
Thanks a lot for the tip! Turns out I had one space after the last ending "EOF" tag. Once I removed the space, everything started working again!

---

