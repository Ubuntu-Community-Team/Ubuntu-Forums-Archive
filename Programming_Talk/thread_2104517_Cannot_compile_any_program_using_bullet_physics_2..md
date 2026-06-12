---
title: "Cannot compile any program using bullet physics 2.80"
date: 2013-01-13
forum: Programming Talk
---

### Post by SGFzc2U= on 2013-01-13
Hello. When I try to compile this program:
```

#include <bullet/btBulletDynamicsCommon.h>
int main(){
    return 0;
}

```g++ gives me this:
```

In file included from /usr/local/include/bullet/btBulletCollisionCommon.h:22:0,
                 from /usr/local/include/bullet/btBulletDynamicsCommon.h:20,
                 from error.cpp:1:
/usr/local/include/bullet/BulletCollision/CollisionDispatch/btCollisionWorld.h:74:34: fatal error: LinearMath/btVector3.h: No such file or directory
compilation terminated.

```After a while of googling around, I found that adding -I/usr/include/bullet/ fixes that error. However, it introduces multiple new ones:
```

In file included from /usr/local/include/bullet/btBulletCollisionCommon.h:28:0,
                 from /usr/local/include/bullet/btBulletDynamicsCommon.h:20,
                 from error.cpp:1:
/usr/local/include/bullet/BulletCollision/CollisionShapes/btCapsuleShape.h: In member function 'virtual void btCapsuleShape::getAabb(const btTransform&, btVector3&, btVector3&) const':
/usr/local/include/bullet/BulletCollision/CollisionShapes/btCapsuleShape.h:68:44: error: 'class btVector3' has no member named 'dot3'
In file included from /usr/local/include/bullet/btBulletCollisionCommon.h:46:0,
                 from /usr/local/include/bullet/btBulletDynamicsCommon.h:20,
                 from error.cpp:1:
/usr/local/include/bullet/BulletCollision/CollisionDispatch/btSphereSphereCollisionAlgorithm.h: In member function 'virtual btCollisionAlgorithm* btSphereSphereCollisionAlgorithm::CreateFunc::CreateCollisionAlgorithm(btCollisionAlgorithmConstructionInfo&, const btCollisionObjectWrapper*, const btCollisionObjectWrapper*)':
/usr/local/include/bullet/BulletCollision/CollisionDispatch/btSphereSphereCollisionAlgorithm.h:59:75: error: cannot allocate an object of abstract type 'btSphereSphereCollisionAlgorithm'
In file included from /usr/local/include/bullet/btBulletCollisionCommon.h:46:0,
                 from /usr/local/include/bullet/btBulletDynamicsCommon.h:20,
                 from error.cpp:1:
/usr/local/include/bullet/BulletCollision/CollisionDispatch/btSphereSphereCollisionAlgorithm.h:29:7: note:   because the following virtual functions are pure within 'btSphereSphereCollisionAlgorithm':
In file included from /usr/local/include/bullet/BulletCollision/CollisionDispatch/btActivatingCollisionAlgorithm.h:19:0,
                 from /usr/local/include/bullet/BulletCollision/CollisionDispatch/btSphereSphereCollisionAlgorithm.h:19,
                 from /usr/local/include/bullet/btBulletCollisionCommon.h:46,
                 from /usr/local/include/bullet/btBulletDynamicsCommon.h:20,
                 from error.cpp:1:
/usr/include/bullet/BulletCollision/BroadphaseCollision/btCollisionAlgorithm.h:72:15: note:     virtual void btCollisionAlgorithm::processCollision(btCollisionObject*, btCollisionObject*, const btDispatcherInfo&, btManifoldResult*)
In file included from /usr/local/include/bullet/BulletDynamics/Dynamics/btDiscreteDynamicsWorld.h:20:0,
                 from /usr/local/include/bullet/btBulletDynamicsCommon.h:22,
                 from error.cpp:1:
/usr/local/include/bullet/BulletDynamics/Dynamics/btDynamicsWorld.h: At global scope:
/usr/local/include/bullet/BulletDynamics/Dynamics/btDynamicsWorld.h:152:2: error: 'btContactSolverInfoDoubleData' does not name a type
/usr/local/include/bullet/BulletDynamics/Dynamics/btDynamicsWorld.h:159:2: error: 'btContactSolverInfoFloatData' does not name a type

```I couldn't find a fix for this from google.

I installed bullet from the default Ubuntu repos.

---

### Post by MadCow108 on 2013-01-13
the local in here:
/usr/**local**/include/bullet/
means it can't be a package installation, those go into /usr/include.
your own local installation may be outdated or broken

with the package you should compile with:
g++ $(pkg-config --cflags bullet) file.cpp $(pkg-config --libs bullet)
and drop the bullet prefix from the #include:
```
#include <btBulletDynamicsCommon.h>
int main(){
    return 0;
}
```

---

### Post by SGFzc2U= on 2013-01-14
:oops: I forgot to mention that I tried to install bullet from source first. That didn't work(The same LinearMath/btVector3.h problem). Then I installed it from the repos. I tried your solution with this messy install, but I got the same errors. So I removed the bullet installed from the repos and reinstalled it from the source. Now your suggestion works very well! :)

---

