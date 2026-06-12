---
title: "Grammar Parser for Java?"
date: 2010-12-13
forum: Programming Talk
---

### Post by SNYP40A1 on 2010-12-13
I need to parse a config file which is made up mostly of blocks which represent a test execution flow.  Generally, it looks like this:

Test node1
{
    vectors = "node1_test";
    level = "nom_lev";
    timing = "nom_timing";
}

Test node2
{
   //similar arguments as above
}

Node node1 node1_test
{
    Port 0
    {
        GoTo node2;
        IncrementCounter fail_node1_test;
    }
    Port 1
    {
        GoTo node2;
        IncrementCounter pass_node_1_test;
    }
}

Node node2 node2_test
{
   ...and so on...
}

There's not a whole lot more to it than that...I would like to construct a graph in memory where I plan to represent each node instance and each node flow as a class.  What would be the easiest Java grammar parser to setup for this task?  I used Lex and Yacc a few years ago for C and thought the configs were a bit complicated, but maybe that's mostly C that I was remembering.  Anyhow, I need to get something working this week, don't have much time to mess around.

---

