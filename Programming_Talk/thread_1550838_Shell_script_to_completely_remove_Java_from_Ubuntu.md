---
title: "Shell script to completely remove Java from Ubuntu 10.04"
date: 2010-08-11
forum: Programming Talk
---

### Post by misha680 on 2010-08-11
This is necessary as I need Sun JDK for OpenMRS development ([www.openmrs.org](www.openmrs.org)).

Applications->Accessories->Terminal

```

touch /tmp/completely-remove-java
chmod +x /tmp/completely-remove-java
gedit /tmp/completely-remove-java

```

Enter the following text:
```

#!/bin/bash
#
# For Ubuntu 10.04

# Remove all Java packages
sudo aptitude purge `dpkg -l | grep java | awk '{print $2}'` -y
sudo aptitude purge `dpkg -l | grep gcj | awk '{print $2}'` -y

# Remove residual configurations
sudo aptitude purge `dpkg -l | grep -e ^rc | awk '{print $2}'` -y

```

File->Save. File->Quit.

Back to Terminal.
```

/tmp/completely_remove_java

```

Misha

---

### Post by dmizer on 2010-08-14
Moved to programming talk. Thank you for posting this.

---

### Post by misha680 on 2010-08-14
> **dmizer said:**
> Moved to programming talk. Thank you for posting this.

No worries. Glad to help and as I previously (forgot) to mention I take _no_ responsibility for what Java-dependent apps this might get rid of on your system.

Misha

---

