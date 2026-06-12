---
title: "How to compile a ns-3 simulation code which uses GMP library"
date: 2013-06-25
forum: Packaging and Compiling Programs
---

### Post by Sagar d on 2013-06-25
[COLOR=#000000][FONT=arial]Hi,[/FONT][/COLOR]

[COLOR=#000000][FONT=arial]This is regarding a compilation issue in ns-3 which I have [/FONT][/COLOR][COLOR=#000000][FONT=arial]encountered. I am doing a research project in which it is required to [/FONT][/COLOR][COLOR=#000000][FONT=arial]implement PKI in AODV. GMP library is used in ns-3 to extend the[/FONT][/COLOR]
[COLOR=#000000][FONT=arial]packet sizes of AODV routing protocol packets in the process to [/FONT][/COLOR][COLOR=#000000][FONT=arial]include big integers in the packet formats. But I am clueless about[/FONT][/COLOR]
[COLOR=#000000][FONT=arial]the compilation of the code using ./waf. [/FONT][/COLOR][COLOR=#000000][FONT=arial]
I want to ask that like a C++ code can be compiled using g++ using the command:
        g++ filename.cc -lgmpxx -lgmp

How can I compile the ns-3 simulation code using ./waf ? Are there any
options available ?

[FONT=arial][COLOR=#000000]Are there any other library available which can be used to implement big integers in ns-3 simulation code and can be compiled easily. Please update me.[/COLOR][/FONT]
[/FONT][/COLOR]
[COLOR=#000000][FONT=arial][FONT=arial][COLOR=#000000]
[/COLOR][/FONT][/FONT][/COLOR]
[COLOR=#000000][FONT=arial][FONT=arial][COLOR=#000000]Thanks.[/COLOR][/FONT][/FONT][/COLOR]

---

### Post by oldos2er on 2013-06-25
Moved to Packaging & Compiling Programs.

---

### Post by Sagar d on 2013-06-26
Thanks Ann

---

### Post by UngodlySpoon on 2013-07-12
I've done some work in ns-3 that required linking the Boost libraries, so perhaps the same approach will work for you.  Inside the wscript for my module, I've got:
```
[COLOR=#333333][FONT=Consolas]**def**[/FONT][/COLOR][COLOR=#333333][FONT=Consolas] [/FONT][/COLOR][COLOR=#990000][FONT=Consolas]**build**[/FONT][/COLOR][COLOR=#333333][FONT=Consolas]([/FONT][/COLOR][COLOR=#333333][FONT=Consolas]bld[/FONT][/COLOR][COLOR=#333333][FONT=Consolas]):[/FONT][/COLOR]
    module **=** bld**.**create_ns3_module([COLOR=#DD1144]'geocron'[/COLOR], [[COLOR=#DD1144]'core'[/COLOR], [COLOR=#DD1144]'network'[/COLOR], [COLOR=#DD1144]'internet'[/COLOR], [COLOR=#DD1144]'applications'[/COLOR], [COLOR=#DD1144]'mobility'[/COLOR], [COLOR=#DD1144]'nix-vector-routing'[/COLOR], [COLOR=#DD1144]'topology-read'[/COLOR], [COLOR=#DD1144]'point-to-point'[/COLOR], [COLOR=#DD1144]'brite'[/COLOR],
                                               [COLOR=#999988]*#these only needed for Test Suite*[/COLOR]
                                               [COLOR=#DD1144]'point-to-point-layout'[/COLOR]
                                               ])
    module**.**lib **=** [[COLOR=#DD1144]'boost_system'[/COLOR], [COLOR=#DD1144]'boost_filesystem'[/COLOR]] [COLOR=#999988]*#needed for scratch to use boost libs*[/COLOR]


    module**.**source, headers_list **=** get_all_sources(bld**.**path**.**relpath())


    module_test **=** bld**.**create_ns3_module_test_library([COLOR=#DD1144]'geocron'[/COLOR])
    module_test**.**source **=** [
        [COLOR=#DD1144]'test/geocron-test-suite.cc'[/COLOR],
        ]
    
    headers **=** bld**.**new_task_gen(features**=**[[COLOR=#DD1144]'ns3header'[/COLOR]])
    headers**.**module **=** [COLOR=#DD1144]'geocron'[/COLOR]
    headers**.**source **=** headers_list


    **if** bld**.**env**.**ENABLE_EXAMPLES:
        bld**.**add_subdirs([COLOR=#DD1144]'examples'[/COLOR])


[COLOR=#333333][FONT=Consolas]    [/FONT][/COLOR][COLOR=#999988][FONT=Consolas]*# bld.ns3_python_bindings()*[/FONT][/COLOR]
```

Notice specifically the line:
```
[COLOR=#333333][FONT=Consolas]module[/FONT][/COLOR][COLOR=#333333][FONT=Consolas]**.**[/FONT][/COLOR][COLOR=#333333][FONT=Consolas]lib[/FONT][/COLOR][COLOR=#333333][FONT=Consolas] [/FONT][/COLOR][COLOR=#333333][FONT=Consolas]**=**[/FONT][/COLOR][COLOR=#333333][FONT=Consolas] [/FONT][/COLOR][COLOR=#333333][FONT=Consolas][[/FONT][/COLOR][COLOR=#DD1144][FONT=Consolas]'boost_system'[/FONT][/COLOR][COLOR=#333333][FONT=Consolas],[/FONT][/COLOR][COLOR=#333333][FONT=Consolas] [/FONT][/COLOR][COLOR=#DD1144][FONT=Consolas]'boost_filesystem'[/FONT][/COLOR][COLOR=#333333][FONT=Consolas]][/FONT][/COLOR]
```

This tells waf to link these two boost libraries, so just replace them with the name of the libraries you need to link.  Hope this helps!

---

