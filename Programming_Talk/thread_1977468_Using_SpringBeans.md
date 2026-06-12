---
title: "Using SpringBeans?"
date: 2012-05-10
forum: Programming Talk
---

### Post by fallenshadow on 2012-05-10
Hey guys/gals,

Does anyone know how to use a springbean instead of using setters for the information?

For example instead of:

```
exampleDetails.setName("bob");
```

I want to use this for the details:

```
<bean id="Details" class="com.examplePackage.Details">
		<property name="name" value="bob" />
	</bean>

```

Thanks in advance!

---

### Post by r-senior on 2012-05-10
That looks ok to me. Did you have a question -- or is this solved?

---

### Post by fallenshadow on 2012-05-12
Yes I got this solved. My spring context file was not in the build path, so after moving it this worked. :)

---

