---
title: "[Python] Class methods vs functions"
date: 2011-10-31
forum: Programming Talk
---

### Post by Erdaron on 2011-10-31
I would like to ask for some general guidance on this question.

I'm working on a project to build an optical ray-tracing program. Not the same as a graphics package, such as POV-Ray, but something that models ray propagation in a lens system. My eventual goal is a GUI-driven program that would be easy to use in an educational environment, or as a fast first-order design tool in non-critical applications.

The core of the program is sequential surface object. The approach treats a lens system as a sequence of spaces and surfaces. The object belongs to a custom class that I am writing.

Creating a class takes information describing the sequence of spaces (lengths and indices of refraction) and surfaces (curvatures). The class then calculates [matrices]("http://en.wikipedia.org/wiki/ABCD_matrix_analysis") representing each element, and one matrix representing the whole system.

A point of internal contention that I have encountered is what other functions should I include as class methods, and what functions should be defined externally. For example, a function that returns position of each ray at every surface in the system rather than just its final position? Or functions that compute other alternative representations (such as Gaussian reduction or cardinal points and planes)? Or functions that compute propagation in a different way (tNYU trace instead of ABCD matrices)? Partial or reverse propagation?

Is there any guidance on what should distinguish a method from a function?

---

### Post by ofnuts on 2011-10-31
> **Erdaron said:**
> Is there any guidance on what should distinguish a method from a function?Define your classes first. Do you have lenses that bend light rays, or light rays that are bent by lenses? Can you define a generic Lens that can be either a SimpleLens or a CompositeLens, and where you can define a CompositeLens as the association of two Lens (Simple or Composite) and a distance...  Once you have the right classes, the methods sort of come out naturally...

---

### Post by 11jmb on 2011-10-31
The methods should intuitively represent what you want your objects to do. Once you decide how to organize your data model into different classes, it should be pretty easy to figure out what each class should be capable of.

Functions should perform a more general (not specifically associated with a class) task. For example, "compare phase of two waves" or "sort waves by amplitude". These would be better handled by a static function rather than a class method.

---

### Post by Erdaron on 2011-10-31
Thank you for the responses!

> **ofnuts said:**
> Define your classes first. Do you have lenses that bend light rays, or light rays that are bent by lenses? Can you define a generic Lens that can be either a SimpleLens or a CompositeLens, and where you can define a CompositeLens as the association of two Lens (Simple or Composite) and a distance...  Once you have the right classes, the methods sort of come out naturally...

In a sequential ray trace, you usually define a system in the following way:
```
Space 0: thickness, material (index of refraction)
Surface 0: curvature (inverse of radius)
Space 1: thickness, material
Surface 1: curvature
etc.
```

So the simplest example, a single lens in air, would be made up of five elements: three spaces and two surfaces. This is a standard approach in optical engineering. It works for simple systems, and scales easily for arbitrarily complex systems.

A ray is normally represented as a 2x1 matrix (N rays would be a 2xN matrix), so it doesn't need its own class as I'm using the matrix implementation from numpy.

@11jmb - what about alternative ways of doing the same thing? Is it alright to use a method to describe the standard way of doing something and then functions for the alternative ways?

---

### Post by ofnuts on 2011-10-31
> **Erdaron said:**
> Thank you for the responses!



In a sequential ray trace, you usually define a system in the following way:
```
Space 0: thickness, material (index of refraction)
Surface 0: curvature (inverse of radius)
Space 1: thickness, material
Surface 1: curvature
etc.
```So the simplest example, a single lens in air, would be made up of five elements: three spaces and two surfaces. This is a standard approach in optical engineering. It works for simple systems, and scales easily for arbitrarily complex systems.OK, so use an OpticalSystem class.

> **Erdaron said:**
> A ray is normally represented as a 2x1 matrix (N rays would be a 2xN matrix), so it doesn't need its own class as I'm using the matrix implementation from numpy.Possibly. But classes can have very simple attributes. 

> **Erdaron said:**
> @11jmb - what about alternative ways of doing the same thing? Is it alright to use a method to describe the standard way of doing something and then functions for the alternative ways?A class can have several methods, all doing similar things. Or you can have a some generic RayTrace class, that defines a method to bend a LighRay using a set of OpticalSystems, and overload that method to implement your various ways to perform your computation. The advantage is tha the generic stuff is done only once in the generic class (for instance processing a whole set of rays) while the specific is restricted to a couple of methods.

---

### Post by nvteighen on 2011-11-01
The line is less clearer than it may seem.

IMO, think about this in the opposite direction. In your head or wherever, design each procedure as a function. Now, if the function always requires an argument of a certain class in order to work, chances are very high that it should be a method of that class.

---

### Post by Erdaron on 2011-11-04
> **nvteighen said:**
> The line is less clearer than it may seem.

IMO, think about this in the opposite direction. In your head or wherever, design each procedure as a function. Now, if the function always requires an argument of a certain class in order to work, chances are very high that it should be a method of that class.

Thank you. This is actually a very helpful perspective.

---

