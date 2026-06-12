---
title: "phony targets"
date: 2012-12-08
forum: Programming Talk
---

### Post by IAMTubby on 2012-12-08
Hey,
I have a question regarding phony targets.

Assume my makefile is as follows
```

hello : hello.c
        gcc -o hello hello.c
clean :
        rm -rf hello

```
When I have a filed called clean in the directory, it gives me the output 
```

make: `clean' is up to date.

```

Fair enough, I know that's because,
"If the name of a target exists as a file, then make will associate the target with the file in the dependancy graph."

**But my question is**, "Does this hold good if 
1)The file is mentioned as a dependency to some target in the makefile, so that the makefile recognizes this file. That would have made sense, as make would form a dependency graph for the targets it encounters as it parses the makefile.

2)Or is it enough if the file is present anywhere in the file system? That doesn't sound right but that's what I'm noticing now. I did a touch clean in the same directory from where I'm running the make, and though the makefile has no reference to this file anywhere, it still gives me the same message that make clean is upto date. So my question is, **why should make even bother about the file called clean, as I'm not saying anything about this file in the makefile.**

Thanks.

PS : I know this can be solved using phony targets, but would like to understand how it works.

---

### Post by dwhitney67 on 2012-12-08
> **IAMTubby said:**
> Hey,
**why should make even bother about the file called clean, as I'm not saying anything about this file in the makefile.**


Think of it as a feature of make.  This feature is sometimes used to mark that a rule as been previously fired.  For instance, if you are performing a build task using a Makefile that requires steps 'one', 'two', and 'three' to be completed in order, something like this is done:
```

all : one two three

one :
        # do something for 1

two :
        # do something for 2

three :
        # do something for 3

```
If the build process should fail during step 'two' or 'three', it would be fruitless to perform step 'one' again after the issue has been corrected.  Thus a common technique is to touch a file bearing the same name as the rule that has been fired and that completed successfully.  So, with that in mind, the Makefile above would look something like:
```

all : one two three

one :
        # do something for 1
        @ touch $@

two :
        # do something for 2
        @ touch $@

three :
        # do something for 3
        @ touch $@

```
Without the touch commands above, each time make is invoked, all the rules would be repeated.

P.S.  Don't convince yourself into believing that Makefiles are for building source code only; it can also be used for shell-scripting purposes.

Here's a Makefile I once worked on to build Cross-Compiled Linux From Scratch (CLFS):
```

#
# SOURCES Makefile
#

ISO_IMAGE = image_system_`date +%G%m%d`RC1.iso


# DEFAULT ENTRY POINT TO DISPLAY USAGE
all help:
	@echo
	@echo "Usage: make [system] ISO_IMAGE=<iso-name>"
	@echo
	@echo "where: system   = cfm | coolcap"
	@echo "       iso-name = name of the ISO image to create (e.g. $(ISO_IMAGE))."
	@echo


# BUILDS AN OLYMED LINUX DISTRO for EITHER CFM or COOL-CAP
cfm coolcap: .system
	@echo "Entering stage to build $@..."
	@sh ${OLY_LFS}/sources/scripts/config-i586.sh enable
	@sh ${OLY_LFS}/sources/scripts/enter-chroot-iso.sh $@ $(ISO_IMAGE) || exit 1
	@sh ${OLY_LFS}/sources/scripts/config-i586.sh disable


# RESTORES SOURCES DISTRIBUTION TO ORIGINAL STATE
distclean: .verify .umnt-kernel-fs
	@sh ${OLY_LFS}/sources/scripts/config-i586.sh disable
	make -C ${OLY_LFS}/sources/build-cross-tools $@
	make -C ${OLY_LFS}/sources/build-tools $@
	make -C ${OLY_LFS}/sources/build-clfs $@
	make -C ${OLY_LFS}/sources/build-cd-os $@
	make -C ${OLY_LFS}/sources/build-iso $@
	@echo Done with $@.


# REMOVES OLY-LFS and RESTORES SOURCES DISTRIBUTION TO ORIGINAL STATE
realclean: distclean
	make -C ${OLY_LFS}/sources/build-cd-os $@
	@$(RM) -r ${OLY_LFS}/cross-tools ${OLY_LFS}/tools /cross-tools /tools
	@sh ${OLY_LFS}/sources/scripts/destroy-dirs.sh
	@for file in .system .verify .setup .cross-tools .tools .mnt-kernel-fs .stripped .clfs1 .clfs2 .clfs3 .olymed .cd-os .umnt-kernel-fs; do $(RM) $$file; done
	@echo
	@echo Done with $@.


##################################################################################
#                                                                                #
# DO NOT CALL ANY OF THE ENTRY POINTS BELOW, UNLESS YOU KNOW WHAT YOU ARE DOING. #
#                                                                                #
##################################################################################

# MAKES CROSS-COMPILER, TOOLS, CLFS, BLFS, and FINALLY OLYMED LINUX
.system: .olymed .umnt-kernel-fs
	@touch $@


# OLYMED STAGE
.olymed: .cd-os
	@echo "Entering stage to add OlyMed system files..."
	@sh ${OLY_LFS}/sources/scripts/config-i586.sh enable
	@sh ${OLY_LFS}/sources/scripts/enter-chroot-olymed.sh || exit 1
	@sh ${OLY_LFS}/sources/scripts/config-i586.sh disable
	touch $@


# CD OS STAGE
.cd-os: .clfs3
	@echo "Entering stage to build CD OS..."
	@sh ${OLY_LFS}/sources/scripts/config-i586.sh enable
	@sh ${OLY_LFS}/sources/scripts/enter-chroot-cd-os.sh || exit 1
	@sh ${OLY_LFS}/sources/scripts/config-i586.sh disable
	touch $@


# CLFS STAGE 3
.clfs3: .stripped
	@echo "Entering 3rd stage of CLFS build..."
	@sh ${OLY_LFS}/sources/scripts/config-i586.sh enable
	@sh ${OLY_LFS}/sources/scripts/enter-chroot-clfs.sh 3 || exit 1
	@sh ${OLY_LFS}/sources/scripts/config-i586.sh disable
	touch $@


# STRIP CLFS LIBRARIES and BINARIES
.stripped: .clfs2
	@echo "Stripping CLFS libraries and binaries..."
	@sh ${OLY_LFS}/sources/scripts/config-i586.sh enable
	@sh ${OLY_LFS}/sources/scripts/enter-chroot-strip.sh || exit 1
	@sh ${OLY_LFS}/sources/scripts/config-i586.sh disable
	touch $@

# CLFS STAGE 2
.clfs2: .clfs1
	@echo "Entering 2nd stage of CLFS build..."
	@sh ${OLY_LFS}/sources/scripts/config-i586.sh enable
	@sh ${OLY_LFS}/sources/scripts/enter-chroot-clfs.sh 2 || exit 1
	@sh ${OLY_LFS}/sources/scripts/config-i586.sh disable
	touch $@


# CLFS STAGE 1
.clfs1: .tools .mnt-kernel-fs
	@echo "Entering 1st stage of CLFS build..."
	@sh ${OLY_LFS}/sources/scripts/config-i586.sh enable
	@sh ${OLY_LFS}/sources/scripts/enter-chroot-clfs.sh 1 || exit 1
	@sh ${OLY_LFS}/sources/scripts/config-i586.sh disable
	touch $@


# BUILD TEMPORARY SYSTEM (TOOLS)
.tools: .cross-tools
	@echo "Building temporary system..."
	make -C ${OLY_LFS}/sources/build-tools install
	touch $@


# BUILD CROSS-TOOLS
.cross-tools: .setup
	@echo "Building cross-tools..."
	make -C ${OLY_LFS}/sources/build-cross-tools install
	touch $@


# ENVIRONMENT SETUP
.setup: .verify
	@echo "Creating cross-tools and tools directories..."
	@mkdir -pv ${OLY_LFS}/cross-tools
	@mkdir -pv ${OLY_LFS}/tools
	@[ -d /cross-tools ] || ln -sv ${OLY_LFS}/cross-tools /
	@[ -d /tools ] || ln -sv ${OLY_LFS}/tools /
	touch $@


# VERIFY PRIVILEGES
.verify:
	@sh ${OLY_LFS}/sources/scripts/verify.sh || exit 1
	@touch $@


# MOUNT VIRTUAL KERNEL FILE SYSTEM
.mnt-kernel-fs:
	@echo "Mounting virtual kernel file system..."
	@sh ${OLY_LFS}/sources/scripts/mnt-kernel-fs.sh
	touch $@


# UNMOUNT VIRTUAL KERNEL FILE SYSTEM
.umnt-kernel-fs:
	@echo "Un-mounting virtual kernel file system..."
	@-sh ${OLY_LFS}/sources/scripts/umnt-kernel-fs.sh
	@rm -f .mnt-kernel.fs
	@touch $@


.PHONY: all cfm coolcap distclean realclean

```

---

### Post by IAMTubby on 2012-12-08
> **dwhitney67 said:**
> Think of it as a feature of make.  This feature is sometimes used to mark that a rule as been previously fired. 
dwhitney, thanks for the explanation about touch. Found it very useful. But my original post was actually asking how make gets to know of a file called clean, although there is no mention of it in the makefile. How then, does it become a part of the dependancy graph, and result in saying 'make : clean : upto date'.

I understand that the reason it says upto date is because clean is a phony target which is always upto date as there are no dependancies. But I still do not understand how the file 'clean' becomes part of the dependancy graph.

Thanks.

---

### Post by dwhitney67 on 2012-12-08
> **IAMTubby said:**
> ... how make gets to know of a file called clean, although there is no mention of it in the makefile.

Perhaps you are right; I misunderstood your question.  You will need to elaborate more, because surely when you state that 'clean' is not known by the Makefile, you are stating something contrary to this type of Makefile:
```

...

clean:
        # do clean up work

```

---

### Post by IAMTubby on 2012-12-08
> **dwhitney67 said:**
> Perhaps you are right; I misunderstood your question.  You will need to elaborate more, because surely when you state that 'clean' is not known by the Makefile, you are stating something contrary to this type of Makefile:
```

...

clean:
        # do clean up work

```
dwhitney, No, I'm sorry. I was very confused myself.
Your reply solved the issue.. almost! . So, make adds clean to the dependency graph on seeing this line ? **clean:**

My only question remains,
After seeing the phony target clean, where then does make check if a file called clean exists ? a)entire file system OR b)directory where makefile exists.

If the answer is b), isn't that "not enough", because in my makefile I could be running files/headers from a lot of locations and not just the current directory. If the answer is a), isn't that too much ?

Please advise.
Thanks.

---

### Post by dwhitney67 on 2012-12-08
> **IAMTubby said:**
> 
My only question remains,
After seeing the phony target clean, where then does make check if a file called clean exists ? a)entire file system OR b)directory where makefile exists.

If the answer is b), isn't that "not enough", because in my makefile I could be running files/headers from a lot of locations and not just the current directory. If the answer is a), isn't that too much ?

Please advise.
Thanks.

I think your questions will be answered if you carefully read the following information:  [http://www.gnu.org/software/make/manual/make.html#index-phony-targets-202](http://www.gnu.org/software/make/manual/make.html#index-phony-targets-202)

For the entire of the document, here's the link:  [http://www.gnu.org/software/make/manual/make.html](http://www.gnu.org/software/make/manual/make.html)

---

### Post by IAMTubby on 2012-12-10
> **dwhitney67 said:**
> I think your questions will be answered if you carefully read the following information:  [http://www.gnu.org/software/make/manual/make.html#index-phony-targets-202](http://www.gnu.org/software/make/manual/make.html#index-phony-targets-202)

For the entire of the document, here's the link:  [http://www.gnu.org/software/make/manual/make.html](http://www.gnu.org/software/make/manual/make.html)
dwhitney67, thanks a lot for the resources, but I need some time to read that and get back to you. I shall try my best to understand and get back to you if I still can't figure out.

Thanks.

---

