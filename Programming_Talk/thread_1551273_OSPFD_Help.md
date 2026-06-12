---
title: "OSPFD Help"
date: 2010-08-12
forum: Programming Talk
---

### Post by mhaider2 on 2010-08-12
Hi,

I got problem while trying to compile OSPFD for linux:

../src/dbage.C: In member function ‘virtual void DBageTimer::action()’:
../src/dbage.C:117: error: ‘GetNextAdj’ was not declared in this scope
../src/dbage.C: In member function ‘void OSPF::checkages()’:
../src/dbage.C:270: warning: deprecated conversion from string constant to ‘char*’

so basically i checked dbage.C and found that:

void DBageTimer::action()

{
    LSA *lsap;
    LsaListIterator iter(&ospf->replied_list);

    // Age the link-state database
    ospf->dbage();
    // Exit helper mode?
    if (ospf->topology_change)
        ospf->htl_topology_change();
    // Delete down neighbors
    ospf->delete_down_neighbors();
    // Establish more adjacencies?
    while (ospf->n_lcl_inits < ospf->max_dds) {
        SpfNbr *np;
       [COLOR=Black] [/COLOR][COLOR=Black]if (!(np = GetNextAdj()))[/COLOR]                            <------Error No 1
            break;
        np->nbr_fsm(NBE_EVAL);
}


AND

void OSPF::checkages()

{
    age_t age;
    int limit;
    LSA *lsap;

    for (age = CheckAge; age < MaxAge; age += CheckAge) {
        uns16 bin;
        bin = Age2Bin(age);
        for (lsap = LSA::AgeBins[bin]; lsap; lsap = lsap->lsa_agefwd) {
            if (!lsap->checkage) {
                lsap->checkage = true;
                dbcheck_list.addEntry(lsap);
            }
        }
    }

    LsaListIterator iter(&dbcheck_list);
    limit = total_lsas/CheckAge + 1;

    for (int i = 0; (lsap = iter.get_next()) && i < limit; i++) {
        if (lsap->valid()) {
            LShdr *hdr;
            int xlen;
            hdr = BuildLSA(lsap);
            xlen = ntoh16(hdr->ls_length) - sizeof(uns16);
            if (!hdr->verify_cksum())
                sys->halt(HALT_DBCORRUPT, "Corrupted LS database");          <--------Error No 2.
               }
        lsap->checkage = false;
        iter.remove_current();
    }

    // Get rid of any invlide entries
    dbcheck_list.garbage_collect();
}
 


can someone help me to solve this problems please.

---

### Post by lordhaworth on 2010-08-12
Focus on the line 117 error. It's been a while since I've used C but its saying that GetNextAdj() is defined out of scope of DBageTimer::action()... so first question is - where else does GetNextAdj() appear in that file?

---

### Post by lordhaworth on 2010-08-12
Actually, looking about it appears that noone has had much luck once encoutnering this problem:

[http://ubuntuforums.org/archive/index.php/t-1087488.html](http://ubuntuforums.org/archive/index.php/t-1087488.html)

[http://www.backports.ubuntuforums.org/showthread.php?t=1087480](http://www.backports.ubuntuforums.org/showthread.php?t=1087480)

You can try what was suggested in these threads but they never said if it worked!

---

### Post by vikas.sood on 2010-08-12
The above 2 threads suggest that ospfd was written for an older kernel. so probably headers differ. I tried to compile the source and get the same error. The problem is method GetNextAdj() is not declared anywhere. 
It is just defined in file src/nbrfsm.C. line number 543
```

SpfNbr *GetNextAdj()
{
    SpfNbr *np;

    if (!(np = ospf->g_adj_head))
        return(0);
    if (!(ospf->g_adj_head = np->n_next_pend))
        ospf->g_adj_tail = 0;

    np->n_adj_pend = false;
    return(np);
}

```

I just added the declaration of GetNextAdj() in nbrfsm.h and it compiles fine. But further there were some errors which i think were related to TCL version required by this package. probably you can look further and solve your problem.

---

### Post by mhaider2 on 2010-08-14
> **lordhaworth said:**
> Actually, looking about it appears that noone has had much luck once encoutnering this problem:

[http://ubuntuforums.org/archive/index.php/t-1087488.html](http://ubuntuforums.org/archive/index.php/t-1087488.html)

[http://www.backports.ubuntuforums.org/showthread.php?t=1087480](http://www.backports.ubuntuforums.org/showthread.php?t=1087480)

You can try what was suggested in these threads but they never said if it worked!

Thanks for giving me feedback.

I also face that problems before but me and my supervisor has sorted out this problems..actually my current problems appeared when we already settle that problem and try to compile ospfd in Linux.

---

### Post by mhaider2 on 2010-08-14
> **vikas.sood said:**
> The above 2 threads suggest that ospfd was written for an older kernel. so probably headers differ. I tried to compile the source and get the same error. The problem is method GetNextAdj() is not declared anywhere. 
It is just defined in file src/nbrfsm.C. line number 543
```

SpfNbr *GetNextAdj()
{
    SpfNbr *np;

    if (!(np = ospf->g_adj_head))
        return(0);
    if (!(ospf->g_adj_head = np->n_next_pend))
        ospf->g_adj_tail = 0;

    np->n_adj_pend = false;
    return(np);
}

```I just added the declaration of GetNextAdj() in nbrfsm.h and it compiles fine. But further there were some errors which i think were related to TCL version required by this package. probably you can look further and solve your problem.

Thanks for the reply.
Can you show me how do you declare GetNextAdj() in nbrfsm.h??

---

