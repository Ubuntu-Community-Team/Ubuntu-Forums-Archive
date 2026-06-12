---
title: "MVC and Collection of Models"
date: 2012-02-21
forum: Programming Talk
---

### Post by RobikShrestha on 2012-02-21
Let us start with an example:

I took it from : [http://codeigniter.com/user_guide/general/models.html](http://codeigniter.com/user_guide/general/models.html)

There is a function get_last_ten_entries() 

(It returns a collection of MODELS from the MODEL itself):

class Blogmodel extends CI_Model{

    function get_last_ten_entries()
    {
        $query = $this->db->get('entries', 10);
        return $query->result();
    }
}

Now we could write the following code:

$entry = new Blogmodel();
$entries = $entry->get_last_ten_entries();

This would use **a Model to fetch similar Models**. Is this a good practice? I mean there is a difference between a collection of Models and the Model itself. A model knowing about a collection of itself does not make sense to me. 

Is it better to keep the function get_last_ten_entries() outside the model? If so where? Do I create another model for this?

---

