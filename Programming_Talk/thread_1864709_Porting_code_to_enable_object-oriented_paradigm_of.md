---
title: "Porting code to enable object-oriented paradigm of C++"
date: 2011-10-19
forum: Programming Talk
---

### Post by alfa_80 on 2011-10-19
I was trying to port a code (talker.cpp) [[http://www.ros.org/wiki/ROS/Tutorials/WritingPublisherSubscriber%28c%2B%2B%29]]("http://www.ros.org/wiki/ROS/Tutorials/WritingPublisherSubscriber%28c%2B%2B%29") into somewhat that of using OO paradigm (C++). By the way, I am not a good  object-oriented programmer but willing to practice a lot and apply in  any projects that I am involved. Here I provide the code and there are  currently 2 problems I am having. They are:


[LIST=1]
[*]Problem with the PointCloud constructor. I got an error of "extra qualification ‘PointCloud::’ on member ‘PointCloud’".
[*]I'm confused the way I should use loop_rate().
[/LIST]
Hopefully, someone who are very good in OO programming can help or improve this little thing..The code:

```

#include "ros/ros.h"
#include "std_msgs/String.h"
#include <sstream>


class PointCloud
{

private:
    int count;
    PointCloud();
    ros::NodeHandle n;
    ros::Publisher chatter_pub;
//    ros::Rate loop_rate(int);
    std_msgs::String msg;
    std::stringstream ss;

public:

    PointCloud::PointCloud()
    {
        chatter_pub = n.advertise<std_msgs::String>("chatter", 1000);
    }
    
    void display();
};

    void PointCloud::display()
    {
//        loop_rate(10);

        count = 0;
        while (ros::ok())
        {
            ss << "hello world " << count;
            msg.data = ss.str();

            ROS_INFO("%s", msg.data.c_str());

            chatter_pub.publish(msg);

            ros::spinOnce();

//            loop_rate.sleep();
            ++count;
        }
    }
int main(int argc, char **argv)
{
    ros::init(argc, argv, "talker");
    PointCloud pointCloud;
    ROS_INFO("Node started");
    ros::spin(); 
    ROS_INFO("Node finished");

  return 0;
}


```

---

### Post by karlson on 2011-10-19
> **alfa_80 said:**
> I was trying to port a code (talker.cpp) [[http://www.ros.org/wiki/ROS/Tutorials/WritingPublisherSubscriber%28c%2B%2B%29]]("http://www.ros.org/wiki/ROS/Tutorials/WritingPublisherSubscriber%28c%2B%2B%29") into somewhat that of using OO paradigm (C++). By the way, I am not a good  object-oriented programmer but willing to practice a lot and apply in  any projects that I am involved. Here I provide the code and there are  currently 2 problems I am having. They are:


[LIST=1]
[*]Problem with the PointCloud constructor. I got an error of "extra qualification ‘PointCloud::’ on member ‘PointCloud’".
[*]I'm confused the way I should use loop_rate().
[/LIST]
Hopefully, someone who are very good in OO programming can help or improve this little thing..The code:


1.  When you are defining functions in class declaration you don't need to Qualify them with Class name.
2.  Have you seen this and done this:
> 
Note: This tutorial assumes that you have completed the previous tutorials: understanding ROS services and parameters.


---

### Post by alfa_80 on 2011-10-19
> **karlson said:**
> 1.  When you are defining functions in class declaration you don't need to Qualify them with Class name.
2.  Have you seen this and done this:

Thanks..I've done no. 1, I've overlooked it that in fact it's in the class declaration itself. But, I still got bugs with that.

---

### Post by alfa_80 on 2011-10-19
It's now solved..Thanks by the way..

---

