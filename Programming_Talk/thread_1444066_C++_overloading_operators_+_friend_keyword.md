---
title: "C++ overloading operators + friend keyword"
date: 2010-03-31
forum: Programming Talk
---

### Post by Drone022 on 2010-03-31
I'm going back to doing stuff in C++ to improve my knowledge of it.

But at the moment I'm stuck, I may be missing something obvious here.

Im creating a 3D vector class called Vector3d. I'm overloading operators so I can use them in relation to vectors.

Here's a few lines from Vectore3d.h
```
friend Vector3d operator/ (const Vector3d& A, const Vector3d& B);
friend Vector3d operator/ (const Vector3d& A, float B);
```

I need them to be friends so they can be used outside the class in the way I want, other wise I get an error informing me I have a binary operator with too many parameters.

But, with the friend keyword in place the compier can't see the definitions at all. In Vector3d.cpp I have :
```
Vector3d Vector3d::operator/ (const Vector3d& A, const Vector3d& B){

	return Vector3d(A.x/B.x, A.y/B.y, A.z/B.z);
}

Vector3d Vector3d::operator/ (const Vector3d& A, float B){
	return Vector3d(A.x/B, A.y/B, A.z/B);
}
```

This gives me: ```
overloaded member function not found in 'Vector3d'
```

What's going on? What am I doing wrong?

---

### Post by geirha on 2010-03-31
Either:
```
class Vector3d {
    ...
    Vector3d operator/ (const Vector3d& v);
};

Vector3d Vector3d::operator/ (const Vector3d& v) {
    return Vector3d(x/v.x, y/v.y, z/v.z);
}

```

or

```

class Vector3d {
    ...
    friend Vector3d operator/ (const Vector3d& a, const Vector3d& b);
};

Vector3d operator/ (const Vector3d& a, const Vector3d& b) {
    return Vector3d(a.x/b.x, a.y/b.y, a.z/b.z);
}

```

---

### Post by schauerlich on 2010-03-31
> **Drone022 said:**
> 
```
Vector3d Vector3d::operator/ (const Vector3d& A, const Vector3d& B){

	return Vector3d(A.x/B.x, A.y/B.y, A.z/B.z);
}

Vector3d **Vector3d::**operator/ (const Vector3d& A, float B){
	return Vector3d(A.x/B, A.y/B, A.z/B);
}
```

When you have a friend function, you want to declare it just as you would any other global function. You do NOT want to include the scope operator - that makes the function a member of the class Vector3d.

---

### Post by Drone022 on 2010-04-01
Thanks guys!

---

