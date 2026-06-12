---
title: "C++  'class fp_core::Element fp_core::Element:Element' is inaccessible"
date: 2012-10-21
forum: Programming Talk
---

### Post by stuckne1 on 2012-10-21
Hello,

I am working on a game engine with a friend and I'm running into a problem with a unit test. I thought I wrote the constructor properly while extending the abstract base class, but I've been dealing with this error for hours and I'm really having difficulty figuring out why. 

I am getting the error... 

/home/steven/gameEngine/fruitpunch/projects/fp_core_test/../fp_core/include/fruitpunch/Elements/Element.h:21:43: error: ‘class fp_core::Element fp_core::Element::Element’ is inaccessible
/home/steven/gameEngine/fruitpunch/projects/fp_core_test/src/Physics/PhysicsJoint.cpp:23:12: error: within this context
/home/steven/gameEngine/fruitpunch/projects/fp_core_test/../fp_core/include/fruitpunch/Elements/Element.h:21:43: error: ‘class fp_core::Element fp_core::Element::Element’ is inaccessible
/home/steven/gameEngine/fruitpunch/projects/fp_core_test/src/Physics/PhysicsJoint.cpp:23:42: error: within this context
make[2]: Leaving directory `/home/steven/gameEngine/fruitpunch/build'
make[1]: Leaving directory `/home/steven/gameEngine/fruitpunch/build'
make[2]: *** [fp_core_test/CMakeFiles/fp_core_test.dir/src/Physics/PhysicsJoint.cpp.o] Error 1
make[1]: *** [fp_core_test/CMakeFiles/fp_core_test.dir/all] Error 2
make: *** [all] Error 2

Here is the cpp file in the unit test where the error is being generated...

```
#include <FpCoreTest.h>
#include <boost/shared_ptr.hpp>
#include <gtest/gtest.h>
#include <fruitpunch/Physics/PhysicsWorld.h>
#include <fruitpunch/Physics/PhysicsJoint.h>
#include <fruitpunch/Elements/Element.h>
#include <fruitpunch/Graphics/Sprite.h>
#include <fruitpunch/Graphics/Primitive.h>



using namespace std;
using namespace boost;
using namespace fp_core::physics;
using namespace fp_core;

// ---------------------------------------------------------------------------
// Stub Class
// ---------------------------------------------------------------------------

class FakeJoint : public PhysicsJoint {
public:
	[COLOR="Red"]FakeJoint(shared_ptr<Element> elementA, shared_ptr<Element> elementB) :[/COLOR]
		PhysicsJoint(elementA, elementB) {
	}
	FakeJoint::ref create() {
		return boost::shared_ptr<b2JointDef>();
	}
private:

};

// ---------------------------------------------------------------------------
// Test Class
// ---------------------------------------------------------------------------

class PhysicsJointTest : public FpCoreTest {
protected:
  shared_ptr<PhysicsWorld> world;

  virtual void SetUp() {
	initEnvironment();
	world = PhysicsWorld::ref(new PhysicsWorld());
	world->init();
  }
};

TEST_F(PhysicsJointTest, Constructor) {
	shared_ptr<Element> sp1(new Sprite());
	shared_ptr<Element> sp2(new Sprite());

	// we need to add a body to each of these...

	// test with bodies

	// and without bodies to test error...

	// these are going to have to have bodies...
	//shared_ptr<FakeJoint> fj = shared_ptr<FakeJoint>(sp1, sp2);
	//world->add(fj);
	/*
	MockContact contact(&sp1, &sp2, world);

	ContactEvent ev(contact, "pre_collide");
	ASSERT_TRUE(ev.getElementA() == sp1);
	ASSERT_TRUE(ev.getElementB() == sp2);
	*/
}

```

Here is the actual PhysicsJoint cpp file...

```
/*
 * PhysicsJoint.cpp
 *
 *  Created on: Sep 9, 2012
 *      Author: leo
 */

#include <fruitpunch/Physics/PhysicsJoint.h>
#include <fruitpunch/Errors/InvalidChildrenError.h>
#include <fruitpunch/Physics/PhysicsWorld.h>

using namespace std;

namespace fp_core {
namespace physics {

PhysicsJoint::PhysicsJoint(shared_ptr<Element> elementA, shared_ptr<Element> elementB) {
    mElementA = elementA;
    mElementB = elementB;
}

PhysicsJoint::~PhysicsJoint() {
    // TODO Auto-generated destructor stub
}

shared_ptr<Body> getBody(shared_ptr<Element>e) {
	boost::shared_ptr< std::vector<boost::shared_ptr<Element> > > children;
	children = e->getChildren();

	// loop through the children and find a body
    vector<shared_ptr<Element> >::iterator it = children->begin();
    for (; it != children->end(); it++) {
    	boost::shared_ptr<Body> b = boost::dynamic_pointer_cast<Body>(*it);

    	if (b) {
    		return b;
    	}
    }

    // might need to add this to runtime instead...
    throw InvalidChildrenError();
}

PhysicsJoint::ref create() {
	return boost::shared_ptr<b2JointDef>();
}

void PhysicsJoint::onAdd() {
	if (typeid(PhysicsWorld) == typeid(*getParent())) {
		getBody(mElementA);
		getBody(mElementB);
		create();
	}
}

shared_ptr<Body> PhysicsJoint::retrieveBodyA() {
	return getBody(mElementA);
}

shared_ptr<Body> PhysicsJoint::retrieveBodyB() {
	return getBody(mElementB);
}

} // namespace fp_core
} // namespace physics

```

---

### Post by spjackson on 2012-10-21
"class ... is inaccessible" usually indicates there's something going on with private inheritance. Without the relevant headers, though, I'm afraid that I can't help any more than that.

---

### Post by stuckne1 on 2012-10-21
Thank you. I'll continuing digging away with that in mind. Here are the the PhysicsJoint.h and Element.h

PhysicsJoint.h

```
/*
 * PhysicsJoint.h
 *
 *  Created on: Sep 9, 2012
 *      Author: leo
 *
 *      Represents a physical joint between two bodies in space.
 *      Abstract class.
 */

#ifndef PHYSICSJOINT_H_
#define PHYSICSJOINT_H_

#include <Box2D/Box2D.h>
#include <boost/shared_ptr.hpp>
#include <fruitpunch/Elements/Element.h>
#include <fruitpunch/Physics/Body.h>
#include <vector>

using namespace boost;

namespace fp_core {
//class Element;

namespace physics {
class PhysicsWorld;
//class Body;

class PhysicsJoint : Element {
public:
	typedef boost::shared_ptr<b2JointDef> ref;

	PhysicsJoint(shared_ptr<Element> elementA, shared_ptr<Element> elementB);
    virtual ~PhysicsJoint();

    //Abstract method responsible for creating a joint
    virtual ref create() = 0;

    virtual void onAdd();

    // Returns the shared_ptr of the Body instance representing the Body that
    // is a children of mElementA/B
    virtual shared_ptr<Body> retrieveBodyA();
    virtual shared_ptr<Body> retrieveBodyB();

private :
    boost::shared_ptr<PhysicsWorld>  mWorld;
    shared_ptr<Element> mElementA;
    shared_ptr<Element> mElementB;
};

} /* namespace physics */
} /* namespace fp_core */
#endif /* PHYSICSJOINT_H_ */

```

Element.h
```
/*
 * Element.h
 *
 *  Created on: 2012-05-21
 *      Author: leo
 */

#ifndef ELEMENT_H_
#define ELEMENT_H_

#include <boost/shared_ptr.hpp>
#include <boost/shared_ptr.hpp>
#include <fruitpunch/Common/Observable.h>
#include <vector>

namespace fp_core {

class Scene;

/// A generic container for everything that goes into a Scene
class Element : public common::Observable {
public:
  typedef boost::shared_ptr<Element> ref;
  typedef boost::shared_ptr< std::vector<Element::ref> > Vector;

  Element();
  virtual ~Element();

  // ---------------------------------------------------------------------------
  // Member Methods
  // ---------------------------------------------------------------------------

  /// Adds an element to the children of the current element.
  /**
   * @return Element::ref the added element
   */
  virtual Element::ref add(Element::ref element);

  /// Removes a child Element equals to the one passed in the argument from the list of children.
  /**
   * @return Element::ref the removed element or a null shared ptr if the element was not found
   */
  virtual Element::ref remove(Element::ref element);

  // ---------------------------------------------------------------------------
  // Callbacks
  // ---------------------------------------------------------------------------
  /// Called when this element has been added to a scene or another element
  virtual void onAdd();

  /// Called when this element is removed from a scene or another element
  virtual void onRemove();

  /// Called by the scene every frame
  virtual void renderFrame();

  /// Called every frame and meant to be overriden
  virtual void onRender();

  // ---------------------------------------------------------------------------
  // Getters and Setters
  // ---------------------------------------------------------------------------
  boost::shared_ptr<Scene> getScene() const;
  void setScene(boost::shared_ptr<Scene> scene);
  boost::shared_ptr<std::vector<Element::ref> > getChildren() const;
  Element::ref getParent() const;
  void setParent(Element::ref parent);

private:
  boost::shared_ptr<Scene> mScene;
  Element::Vector          mChildren;
  Element::ref             mParent;
};

} /* namespace fp_core */
#endif /* ELEMENT_H_ */

```

---

### Post by stuckne1 on 2012-10-21
I was missing [COLOR="Lime"]public[/COLOR] in the PhysicsJoint.h file where next to Element...

```
/*
 * PhysicsJoint.h
 *
 *  Created on: Sep 9, 2012
 *      Author: leo
 *
 *      Represents a physical joint between two bodies in space.
 *      Abstract class.
 */

#ifndef PHYSICSJOINT_H_
#define PHYSICSJOINT_H_

#include <Box2D/Box2D.h>
#include <boost/shared_ptr.hpp>
#include <fruitpunch/Elements/Element.h>
#include <fruitpunch/Physics/Body.h>
#include <vector>

using namespace boost;

namespace fp_core {
//class Element;

namespace physics {
class PhysicsWorld;
//class Body;

class PhysicsJoint : [COLOR="Lime"]public[/COLOR] Element {
public:
	typedef boost::shared_ptr<b2JointDef> ref;

	PhysicsJoint(shared_ptr<Element> elementA, shared_ptr<Element> elementB);
    virtual ~PhysicsJoint();

    //Abstract method responsible for creating a joint
    virtual ref create() = 0;

    virtual void onAdd();

    // Returns the shared_ptr of the Body instance representing the Body that
    // is a children of mElementA/B
    virtual shared_ptr<Body> retrieveBodyA();
    virtual shared_ptr<Body> retrieveBodyB();

private :
    boost::shared_ptr<PhysicsWorld>  mWorld;
    shared_ptr<Element> mElementA;
    shared_ptr<Element> mElementB;
};

} /* namespace physics */
} /* namespace fp_core */
#endif /* PHYSICSJOINT_H_ */
```

---

### Post by spjackson on 2012-10-22
> 
I was missing public in the PhysicsJoint.h file where next to Element...

Ah, so you were unintentionally using private inheritance. I take it that your problem is solved now.

---

### Post by stuckne1 on 2012-10-22
> **spjackson said:**
> Ah, so you were unintentionally using private inheritance. I take it that your problem is solved now.

Yes, it is solved now. Thank you!

---

