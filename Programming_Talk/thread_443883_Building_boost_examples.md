---
title: "Building boost examples?"
date: 2007-05-14
forum: Programming Talk
---

### Post by mikelygee on 2007-05-14
I've installed all the boost and boost-related packages in the Feisty repository. Included are a nice set of examples in /usr/share/doc/libboost-doc/examples, but I've been unable to get them to work. 

I've copied the /usr/share/doc/libboost-doc/examples/libs/spirit to my home directory, and ungzipped all the source files. If I ran "bjam" from the example direcotry, I'm told:

    error: Could not find parent for project at '.'
    error: Didd not find Jamfile or project-root.jam in any parent directory

There is a 'Jamfile' in this directory, but not in the parent, so I tried 'cd'ing to 'fundamental' and running bjam. Now I'm told:

    warning: no toolsets are configured
    .
    .
    .
    error: no Jamfile in current directory found, and no target references specified

Is there a step-by-step guide to getting started with boost in Ubuntu?

Any volunteers to step me through it?

Thanks,
Mike

---

### Post by Mirrorball on 2007-05-14
I don't know what the problem is, but I've always used boost without bjam, like any other library, and it has always worked for me.

---

