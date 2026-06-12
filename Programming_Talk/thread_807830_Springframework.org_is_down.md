---
title: "Springframework.org is down"
date: 2008-05-26
forum: Programming Talk
---

### Post by SupaSonic on 2008-05-26
[http://www.springframework.org/schema/beans](http://www.springframework.org/schema/beans) is down atm, and my spring.xml has the following code ```

<beans xmlns="http://www.springframework.org/schema/beans" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://www.springframework.org/schema/beans http://www.springframework.org/schema/beans/spring-beans-2.5.xsd">
```

On server startup, it crashes because it can't find the schema. Anyone have a local copy of spring-beans-2.5.xsd?

---

### Post by Quikee on 2008-05-26
> **SupaSonic said:**
> [http://www.springframework.org/schema/beans](http://www.springframework.org/schema/beans) is down atm, and my spring.xml has the following code ```

<beans xmlns="http://www.springframework.org/schema/beans" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://www.springframework.org/schema/beans http://www.springframework.org/schema/beans/spring-beans-2.5.xsd">
```

On server startup, it crashes because it can't find the schema. Anyone have a local copy of spring-beans-2.5.xsd?

The schemas are also located in spring-framework zip file (in dist/resources). This is also common as internet is not always available when an application is deployed and spring should validate the configuration every time it starts.

---

