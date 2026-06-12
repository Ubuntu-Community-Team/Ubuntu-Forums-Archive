---
title: "Overriding an Abstract method with generics"
date: 2009-03-30
forum: Programming Talk
---

### Post by coachabower on 2009-03-30
Hi guys, here's my problem.  I have a program due for a class and I can't see why I'm getting an error message.  The logical insides of the method are irrelevant so here are my method declarations.

Abstract Class is as follows,
import java.util.Comparator;
import java.util.List;

public abstract class BT<T>
{

   /**
    * A node in the tree.
    */
   public abstract class BNode
   {
      private T[] keys;

      /**
       * Simulate reading the keys from the disk.
       *
       * @return the keys associated with this node.
       */
      final public T[] diskReadKeys()
      {
         return keys.clone();
      }

      /**
       * Simulate writing the keys to the disk.
       *
       * @param newKeys
       *                the new values for the keys.
       */
      final public void diskWriteKeys(T[] newKeys)
      {
         this.keys = newKeys;
      }
   }

   /**
    * Inserts the specified element to this B-Tree according to the
    * specified comparator.
    *
    * @param element
    *                the element to be inserted, if not present.
    * @param comparator
    */
   abstract public void insert(T element, Comparator<? super T> comparator);

   /**
    * Deletes the specified element from this B-Tree according to the
    * specified comparator.
    *
    * @param element
    *                the element to be deleted, if present.
    * @param comparator
    * @return <tt>true</tt> if the B-tree contained the specified
    *         element.
    */
   abstract public boolean delete(T element, Comparator<? super T> comparator);

   /**
    * Returns the largest key of this B-Tree that is smaller than the
    * specified key value k according to the specified comparator.
    *
    * @param k
    * @param comparator
    * @return the largest key that is less than k or <tt>null</tt> if no
    *         such that key exists.
    */
   abstract public T findMax(T k, Comparator<? super T> comparator);

   /**
    * Returns the smallest key of this B-Tree that is greater than the
    * specified key value k according to the specified comparator.
    *
    * @param k
    * @param comparator
    * @return the smallest key that is greater than k or <tt>null</tt> if
    *         no such that key exists.
    */
   abstract public T findMin(T k, Comparator<? super T> comparator);

   /**
    * Returns the height of this B-Tree.
    *
    * @return the height of the B-tree.
    */
   abstract public int height();

   /**
    * Returns a list containing all of the elements in this B-Tree using
    * tree inorder traversal.
    *
    * @return a list containing all of the elements in this B-tree in
    *         inorder.
    */
   abstract public List<T> getInfixOrder();
}



The Sub Class is as follows, 
public class BTree<T> extends BT {
    private void insert (T element, Comparator<? super T> comp) {
    }
    
    private boolean delete (T element, Comparator<? super T> comp) {
        return true;
    }
    
    private T findMax (T k, Comparator<? super T> comp) {
        return element;
    }
    
    public T findMin(T k, Comparator<? super T> comp) {
        return k;
    }
    
    private int height () {
        return 4;
    }
    
    private List<T> getInfixOrder () {
     return new LinkedList ();
    }
}


My error says BTree is not abstract and does not override the abstract method findMin ( java.lang.Object, Java.util.Comparartor) in BT

As far as I can tell it overrides the method fine, I have the same name for both, same parameters, same return type...The parameter Comparator<? super T> comp is new to me, so idk if I'm supposed to change the ? super T to something else or what.

Any help would be greatly appreciated

---

