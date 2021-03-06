---
layout: post
title: ios CoreData 配置删除级联操作规则
---

### 关系对象间的删除规则

关系对象的删除规则指定，当删除源对象的时候应该怎么处理目标对象。
下面会用部门和职员的例子来解释这些删除规则名词：

####deny

如果至少有一个员工，就不删除部门对象。

e.g. 如果要删除部门对象，那么要保证当前部门的所有员工对象全部转移到其他对象中去（保证部门对象的employees属性为空），否则删除不掉。

####Nullify

只删除关联关系，不删除对象。

一般是一个部门对一个员工是可选属性，或者在你下次进行保存操作前已经为每个员工设置一个新的部门

####Cascade

当你删除源对象时，同时删除目标对象。

e.g. 你删除（解散）部门对象的时候，删除（解雇）所有员工对象。

####NO Action

不做任何操作。

e.g. 如果你删除部门对象，保留所有员工对象，这样员工对象还是认为自己属于被删除的部门对象（单向解除关联）。

