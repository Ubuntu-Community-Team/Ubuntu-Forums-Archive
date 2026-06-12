---
title: "Sometimes .strtab after .symtab? What what whaaa?!?"
date: 2011-02-02
forum: Programming Talk
---

### Post by sigflup on 2011-02-02
I'm noticing that sometimes .strtab is right after symtab (as in, in the actual elf) but there isn't a section header for strtab. 

I'm wondering if this is documented. I've been looking through all the elf docs I can find and haven't found a meaning to strtab not having a section in the section table and symtab still being present. When does this happen?

I wrote an elf-parser to prove that the symtab.sh_name entries are refering to the non-existent strtab and indeed they are. I don't think I'm looking at the elf incorrectly.  I have walked through the section headers manually and also while checking their type flag, not just relying on their textual name. 

Edit: I should also add that when this happened strtab is always at the end of the file

---

