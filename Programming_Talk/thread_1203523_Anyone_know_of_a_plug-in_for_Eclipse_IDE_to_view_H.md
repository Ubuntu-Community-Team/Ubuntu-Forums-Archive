---
title: "Anyone know of a plug-in for Eclipse IDE to view HTML?"
date: 2009-07-03
forum: Programming Talk
---

### Post by SNYP40A1 on 2009-07-03
In some of the .java source code files I am viewing, the comments are in HTML, like this:

[PHP]
**
 * MutateERCPipeline works very similarly to the "Gaussian" algorithm
 * described in Kumar Chellapilla,
 * "A Preliminary Investigation into Evolving Modular Programs without Subtree
 * Crossover", GP98.
 *
 * <p>MutateERCPipeline picks a random node from a random tree in the individual,
 * using its node selector.  It then proceeds to "mutate" every ERC (ephemeral
 * random constant) located in the subtree rooted at that node.  It does this
 * by calling each ERC's <tt>mutateERC()</tt> method.  The default form of <tt>mutateERC()</tt>
 * method is to simply call <tt>resetNode()</tt>, thus randomizing the ERC;
 * you may want to override this default to provide more useful mutations,
 * such as adding gaussian noise.

 <p><b>Typical Number of Individuals Produced Per <tt>produce(...)</tt> call</b><br>
 ...as many as the source produces

 <p><b>Number of Sources</b><br>
 1

 <p><b>Parameters</b><br>
 <table>
 <tr><td valign=top><i>base</i>.<tt>ns</tt>.0<br>
 <font size=-1>classname, inherits and != GPNodeSelector</font></td>
 <td valign=top>(GPNodeSelector for tree)</td></tr>

 <tr><td valign=top><i>base</i>.<tt>tree.0</tt><br>
 <font size=-1>0 &lt; int &lt; (num trees in individuals), if exists</font></td>
 <td valign=top>(tree chosen for mutation; if parameter doesn't exist, tree is picked at random)</td></tr>
 </table>

 <p><b>Default Base</b><br>
 gp.breed.mutate-erc

 <p><b>Parameter bases</b><br>
 <table>
 <tr><td valign=top><i>base</i>.<tt>ns</tt><br>
 <td>The GPNodeSelector selector</td></tr>
 </table>


 * @author Sean Luke
 * @version 1.0 
 */
[/PHP]

Anyone know of a plug-in for Eclipse to view that code as HTML instead of HTML source?

---

### Post by Reiger on 2009-07-03
Those are presumably *Doc comments which will be rendered in a pop up box when you hover over the code they refer to and are just a marked up version of the typical JavaDoc comments:
```

/**
 * @author Reiger
 */
class HellWorld {

  /**
   * Main entry point of Hello World app:
   * @param String[] args (arguments to app)
   */
  public static void main(String [] args) {
    System.out.println("Hello world!");
  }
}

```

---

### Post by SNYP40A1 on 2009-07-03
> **Reiger said:**
> Those are presumably *Doc comments which will be rendered in a pop up box when you hover over the code they refer to and are just a marked up version of the typical JavaDoc comments:
```

/**
 * @author Reiger
 */
class HellWorld {

  /**
   * Main entry point of Hello World app:
   * @param String[] args (arguments to app)
   */
  public static void main(String [] args) {
    System.out.println("Hello world!");
  }
}

```

Ahh, now I understand why the commented in HTML.  Makes sense.  But Eclipse should still have a plug-in for recognizing this in the source code.  Maybe an editor box could pop up or something.

---

### Post by Can+~ on 2009-07-03
It actually has syntax highlighting for the html docs, and when viewing the help on the Autocompletion (Ctrl+Space), it displays it as html.

---

