---
title: "Check if a variable has NOT been initialized"
date: 2011-06-13
forum: Programming Talk
---

### Post by carlos21 on 2011-06-13
Is it possible to check if a variable has not been initialized in C++? Or if a variable HAS been initialized? If so how.

The type would be *int *and anyone with OpenCV experience what happens if:

```

int deviceID;
CvCapture * camera = cvCreateCameraCapture(deviceID);
```Where deviceID has not been initialized, would it just go to default zero?

---

### Post by cgroza on 2011-06-13
The deviceID is initialized to the default value of 0. You only need to worry about this with pointers.

That is why when you create them you initialize them with NULL so you can check them later.

---

### Post by BkkBonanza on 2011-06-13
Well, it depends whether deviceID is local or global. If global then it would be 0 but if local it would be whatever is on the stack - random data.

You should init the variable to some value you know and can test if you need to detect if it has been initialized by other code.

eg.

int deviceID = -1;

... later

if(deviceID != -1)
    camera = cvCreateCameraCapture(deviceID);

---

### Post by krazyd on 2011-06-14
There's a good explanation here: [http://stackoverflow.com/questions/2218254/variable-initialization-in-c/2218275#2218275](http://stackoverflow.com/questions/2218254/variable-initialization-in-c/2218275#2218275)

---

