---
title: "Flex mxml scope"
date: 2008-08-20
forum: Programming Talk
---

### Post by Felson on 2008-08-20
Dose anyone know if there is a way to limit the scope of an item within a container?
Eg:
```

<mx:Box id="myBox">
  <mx:Label id="myLabel">
</mx:Box>

```

I would then want myLabel to be referenced in Action Script as "myBox.myLabel" and be inaccessible as just "myLabel".

---

