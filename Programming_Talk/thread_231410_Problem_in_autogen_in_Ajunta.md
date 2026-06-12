---
title: "Problem in autogen in Ajunta"
date: 2006-08-07
forum: Programming Talk
---

### Post by Alain21 on 2006-08-07
Sometimes when i try to do autgen ... the resulting makefile for my src directory does not generate properly ... and I have to edit it back by hand ..  
The result gives me 
 
[...] 
.PHONY: mostlyclean-libLIBRARIES distclean-libLIBRARIES \ 
clean-libLIBRARIES maintainer-clean-libLIBRARIES uninstall-libLIBRARIES \ 
install-libLIBRARIES mostlyclean-compile distclean-compile \ 
clean-compile maintainer-clean-compile mostlyclean-libtool \ 
distclean-libtool clean-libtool maintainer-clean-libtool tags \ 
mostlyclean-tags distclean-tags clean-tags maintainer-clean-tags \ 
distdir mostlyclean-depend distclean-depend clean-depend \ 
maintainer-clean-depend info-am info dvi-am dvi check check-am \ 
installcheck-am installcheck install-exec-am install-exec \ 
install-data-am install-data install-am install uninstall-am uninstall \ 
all-redirect all-am all installdirs mostlyclean-generic \ 
distclean-generic clean-generic maintainer-clean-generic clean \ 
mostlyclean distclean maintainer-clean 
 
 
\ 
-L/home/alain/Projects/OggVorbisSDK/lib -L/home/alain/Projects/SDL12/lib 
 
[...] 
Which thereafter give a error on compile : "Missing separator. Stop. 

Anyone have any idea how to fix this ? Am I doing something wrong to cause this malfunction ??

---

