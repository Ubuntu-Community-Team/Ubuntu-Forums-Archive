---
title: "APIs and SDKs"
date: 2008-09-17
forum: Programming Talk
---

### Post by Fosfate on 2008-09-17
What exactly is an API or SDK?

IS it a set of commands for a certain language (C, C++, PHP, etc.)?

Also, how come, within hours of an SDK's release (such as the iPhone SDK) are people already coming out with programs for it? Are there people who will download the SDK immediately and play with it for hours to write the first program?

---

### Post by Npl on 2008-09-17
Ever thought of looking it up on Wikipedia ([API]("http://en.wikipedia.org/wiki/API") [SDK]("http://en.wikipedia.org/wiki/SDK")) or googling it?

---

### Post by LaRoza on 2008-09-17
> **Fosfate said:**
> 
Also, how come, within hours of an SDK's release (such as the iPhone SDK) are people already coming out with programs for it? Are there people who will download the SDK immediately and play with it for hours to write the first program?

There could be pre-releases. There could be in house. There could be existing code. And yes, there can be those waiting for it to use it immediately (better than waiting all night in line for the latest iApple iProduct)


> **Npl said:**
> Ever thought of looking it up on Wikipedia ([API]("http://en.wikipedia.org/wiki/API") [SDK]("http://en.wikipedia.org/wiki/SDK")) or googling it?

Normally such responses are discouraged, but asking for a definition asks for it...

@OP Wikipedia is a good place to look for answers, especially for technical things.

---

### Post by Tomosaur on 2008-09-17
> **Fosfate said:**
> What exactly is an API or SDK?

IS it a set of commands for a certain language (C, C++, PHP, etc.)?

Also, how come, within hours of an SDK's release (such as the iPhone SDK) are people already coming out with programs for it? Are there people who will download the SDK immediately and play with it for hours to write the first program?

The beauty of a good API / SDK is that developing something using it doesn't take long - so hopefully that explains how people get something out there so quickly! Most of the time these people will already have some plan of what they want to build, and don't forget that many will have been keeping close to the development of the API / SDK and so are probably well up to date on the documentation and all that jazz.

API = Application Programming Interface. Usually a set of methods that a program can call. Usually used for services which handle large amounts of data (e.g: Google's set of APIs for maps and other stuff). An API is usually used to **connect** applications and allow them to exchange data (not necessarily over the internet). So say you need to pull data from a database, you might use an API to write a program to do that, rather than manually entering every SQL command.

SDK = Software Development Kit. The actual stuff people need to develop software. For example, the Java SDK contains the classes required to develop applications, the compiler etc.

---

### Post by nvteighen on 2008-09-17
An API is the public interface some functions library gives you for use in your program. It's just what a library allows you to do with it. The API usually comes in a human readable form (the API documentation) and a machine-readable, like C and C++'s header files or in scripting languages, the module itself.

IIRC a SDK is a kit of tools to develop stuff for a particular API.

---

