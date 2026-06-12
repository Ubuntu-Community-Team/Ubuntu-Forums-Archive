---
title: "Plotting 2 columns from 2 datesets in QtOctave via programming"
date: 2012-01-06
forum: Programming Talk
---

### Post by alfa_80 on 2012-01-06
I would like to use QtOctave to do plotting. I have 2 datasets in .txt format and would like to plot them in order to compare the values of them with respect to certain column2 in only one 2D coordinate system. In particular, I want to plot all values in column 5 (set as y-axis values) taking values and their column 1 (set as x-axis values) respectively from dataset A and B. The dataset looks like below(a few lines of them): 

```

%time,field.header.seq,field.header.stamp,field.header.frame_id,field.pose.position.x,field.pose.position.y,field.pose.position.z,field.pose.orientation.x,field.pose.orientation.y,field.pose.orientation.z,field.pose.orientation.w
175447000000,5,175447000000,pose,431733.858174,5639759.55765,13.464,0.0419218838249,-0.0300052587638,-0.184327537836,0.981511894425
175467000000,6,175467000000,pose,431733.858174,5639759.55765,13.464,0.0419218838249,-0.0300052587638,-0.184327537836,0.981511894425
175501000000,7,175501000000,pose,431733.858174,5639759.55765,13.464,0.0419218838249,-0.0300052587638,-0.184327537836,0.981511894425
175548000000,8,175548000000,pose,431733.858174,5639759.55765,13.533,0.0449266786318,-0.0775877847456,-0.187770087923,0.978112530994
175567000000,9,175567000000,pose,431733.858174,5639759.55765,13.533,0.0449266786318,-0.0775877847456,-0.187770087923,0.978112530994
175597000000,10,175597000000,pose,431733.858174,5639759.55765,13.533,0.0449266786318,-0.0775877847456,-0.187770087923,0.978112530994
175621000000,11,175621000000,pose,431733.858174,5639759.55765,13.533,0.0449266786318,-0.0775877847456,-0.187770087923,0.978112530994

```I know we can copy and paste the value using GUI-based plotting, but, since I have lots of datasets to treat it would be better if someone who knows to code in QtOctave that read those 2 columns (one for each dataset), and then, plot it.

Thanks in advance.

---

