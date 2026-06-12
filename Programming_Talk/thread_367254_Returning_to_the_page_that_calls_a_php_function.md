---
title: "Returning to the page that calls a php function"
date: 2007-02-21
forum: Programming Talk
---

### Post by Flubs4u on 2007-02-21
I'm just starting out doing php development and I've got a question about getting back to my web page.

I've got a form that posts to a php script in another file.  Something like main.html posts to script.php, the script does it's business and then just displays a blank page.  I want it to return to the page that called it or go to a confirmation page, but I'm not finding the information anywhere.

any help would be appreciated.

---

### Post by Mirrorball on 2007-02-21
```

<?php
header('Location: ' . $absolute_link_to page);
exit;

```

---

### Post by Flubs4u on 2007-02-22
Thanks so much!

---

