---
layout: post
title:  "Cocos2dx UI-序列帧动画位置问题（通过 csb 加载）"
date:   2019-05-13 23:49:34 +0800
categories: [cocos2dx, UI]
tags: [序列帧, 位置]
---

> 背景：在 cocos studio 中编辑好的序列帧动画（例如左右移动等），不要吐槽还在用 cocos studio，很多项目其实都还在用。

先上结论，序列帧动画播放的位置不会随着位置的调整而改变，也就是用来播放动画的那个节点，在播放动画之前位置发生改变的话（例如在播放前改变了父节点的高度，或挪动自己的位置等），在播放序列帧时还是会从原来的位置开始播放及结束。

如果想要改变位置的话，还是直接调整父节点的位置比较好，如果父节点的高度需要实时调整的话（可能需要做内容自适配），那么在父节点和播放动画的节点中间再插入一层节点，使其成为播放动画的父节点，这样就可以在原父节点调整时，影响的是新父节点的位置，而动画节点的位置相对新父节点来说都是保持一样的。（尽量不要在需要播放动画的节点上有直接调整位置的操作，可能达不到想要的预期效果）