---
title: "bash help"
date: 2006-07-28
forum: Programming Talk
---

### Post by cosmo1983 on 2006-07-28
Hi,

I am trying to load url in firefox from bash script. Everything loads up alrite but it doesn't execute the command after loading firefox, seems to be stuck. If I manually close firefox rest of the script executes.

Any help would be appreciated.

```

#!/bin/bash

firefox "http://www.google.com/"

echo "Completed"


```

---

### Post by IYY on 2006-07-28
> **cosmo1983 said:**
> Hi,

I am trying to load url in firefox from bash script. Everything loads up alrite but it doesn't execute the command after loading firefox, seems to be stuck. If I manually close firefox rest of the script executes.

Any help would be appreciated.

```

#!/bin/bash

firefox "http://www.google.com/"

echo "Completed"


```

```

#!/bin/bash

firefox "http://www.google.com/" &

echo "Completed" 


```

---

### Post by cosmo1983 on 2006-07-29
Thanks, worked like a charm.

---

