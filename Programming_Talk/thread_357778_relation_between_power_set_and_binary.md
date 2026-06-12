---
title: "relation between power set and binary"
date: 2007-02-10
forum: Programming Talk
---

### Post by lnostdal on 2007-02-10
```

(defmethod power-set-of ((list list))
  (let ((sets nil) (list-length (length list)))
    (dotimes (counter (expt 2 list-length))
      (let ((set nil))
        (dotimes (index list-length)
          (when (logbitp index counter)
            (push (nth index list) set)))
        (push set sets)))
    sets))

```

recursion/iteration might have turned out better time/space-wise, but this is a fun way of doing it i think :)

(`loop' instead of `dotimes' would probably shorten the code quite a bit.. but generally i don't care; it's only for code-generating code with 6-8 elements anyways :))

how would you guys find a [power set](http://en.wikipedia.org/wiki/Power_set)?

---

