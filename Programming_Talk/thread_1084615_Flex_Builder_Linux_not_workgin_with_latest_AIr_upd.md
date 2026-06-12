---
title: "Flex Builder Linux not workgin with latest AIr update"
date: 2009-03-02
forum: Programming Talk
---

### Post by igkuk7 on 2009-03-02
When trying to run some AIR projects from Flex Builder Linux I got an error message:
> This application requires a version of the Adobe Integrated Runtime (AIR) which is no longer supported. Please contact the application author for an updated version.

I followed the instructions to [update the AIR SDK in Flex Builder Linux]("http://labs.adobe.com/technologies/flex/flexbuilder_linux/releasenotes.html#air"). Now, when I attempt to build any AIR projects I get build errors:
> abc bytecode decoding failed.

Even when creating a new empty project I am unable to build it.

I have tried getting the latest stable Flex SDK and AIR SDK and pointing Flex Builder Linux to them, but that is not working. I have clean installed everything and the problems still exist.

Is there something I am missing when updating the AIR SDK in Flex Builder Linux? Or is there some way to make Flex Builder Linux not give me the original version error?

Thanks in advance for any suggestions.

---

### Post by igkuk7 on 2009-03-03
For completeness:

I managed to find a workaround to this slight bug which can be found at [http://bugs.adobe.com/jira/browse/FBE-323]("http://bugs.adobe.com/jira/browse/FBE-323")

Basically you need to use the airglobal.swc library from the SDK prior to the update, as the updated one is causing the bytecode decoding errors.

---

