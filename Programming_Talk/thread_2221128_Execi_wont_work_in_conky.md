---
title: "Execi wont work in conky"
date: 2014-04-30
forum: Programming Talk
---

### Post by tomasvdmeer on 2014-04-30
Conky:
```

${texeci 1 ~/ping.sh 8.8.8.8}

```

ping.sh
```

#!/bin/bash

if ping -c 1 -W 2 $1 > /dev/null; then
echo "Online!"
else
echo "Offline!"
fi

```

And still execi wont start. How can i fix it..

---

