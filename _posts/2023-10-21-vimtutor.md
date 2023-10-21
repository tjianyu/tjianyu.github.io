---
layout: post
title: Vimtutor总结
categories: [vim]
description: 读了vim的vimtutor，总结下内容
keywords: vim, linux
mermaid: false
sequence: false
flow: false
mathjax: false
mindmap: false
mindmap2: false
---


**按`<ESC>`将置于Normal模式或取消不需要的和部分完成的命令。**
### Lesson 1
- 移动光标：`h`(←),`j`(↓),`k`(↑),`l`(→);
- `:q! <ENTER>`不保存退出;
- `:wq! <ENTER>`保存退出;
- `x`删除光标处的字符;
- `i`在光标前插入文本;
- `A`在行尾追加文本;
---
### Lesson 2
- `dw`从光标处删除到下一个单词;（直至删掉一个空格或者遇到行尾或标点符号）
- `de`从光标处删除到词尾;（直至遇到一个空格或标点符号）
- `d$`从光标处删除到行尾;
- `dd`删除整行;
> change命令格式：`operater[number]motion`  
> - operator是要做什么，比如d表示delete;
> - [number]可选的计数，用于重复动作;
> - motion指在要操作的文本上的移动方式，（没有operater时，光标将按指定方式移动）如：
>>- `w`（直到下一个单词的开头，不包括第一个字符）;
>>- `e`（到当前单词的末尾，包括最后一个字符）;
>>- `$`（到行结束，包括最后一个字符）;
- `0`光标移动到行首;
- `u`撤销一次操作;
- `U`恢复一行为初始状态;
- `<CTRL-R>`重做,撤销一次撤销操作;
---
### Lesson 3
- `p`在光标后放回刚刚删除的文本;（如果删除了一行，则放在光标的下一行）
- `r`后紧接着键入的字符将替换光标处的字符;
> change操作符和delete操作符类似，允许将光标通过motion移动，并置于插入模式。如键入`ce`将光标移到词尾，键入`c$`将光标移动到行尾;
>- 格式：`c[number]motion`;
---
### Lesson 4
- `<CTRL-G>`显示光标在文件中的位置和文件状态，形如 */tmp/tutorfZrEA2" [Modified] line 577 of 971 --59%-- col 20-41* ;
- `[number]G`移动到行号,缺省为移动到文件尾;
- `gg`移动到文件头;
>- `/`后紧跟着输入一个短语，向前搜索该短语;（不包括光标处）
>- `?`后紧跟着输入一个短语，向后搜索该短语;（包括光标处）
在搜索之后，输入`n`以查找同一方向的下一个出现，或`N`查找相反方向的下一个出现。`<CTRL-O>`将到达较老的位置，`<CTRL-I>`到达较新的位置;
- `%`当光标处为(,),[,],{,}，将移动到匹配项。
>- `:s/old/new`将行中的第一个old替换为new;
>- `:s/old/new/g`将行中的所有old替换为new;
>- `:#,#s/old/new/g`将两行之间（包括两行）的所有old替换为new;
>- `:%s/old/new/g`将文件中的所有old替换为new;
>- `:%s/old/new/gc`将文件中的所有old替换为new，c表示确认替换;每次替换前询问：  
*replace with new (y/n/a/q/l/^E/^Y)?*  
其中a表示全部替换(all)，q表示退出(quit)，l表示替换完当前匹配后退出(last)，^E和^Y用于在不移动光标的情况下滚动屏幕，^E表示向下滚动一行`<CTRL-E>`，^Y表示向上滚动一行`<CTRL-Y>`;
---
### Lesson 5
- `:!command`执行外部命令;（`:`将光标设置在屏幕底部，`!`允许执行任何外部shell命令）
- `:w FILENAME`创建文件FILENAME,将当前Vim文件写入;
> `v motion :w FILENAME`创建文件FILENAME,并将高亮选择的文本写入;
>- `v`并移动光标选择文本，选择区域将被高亮显示;
>- `:`屏幕底部出现<,>;
>- `w FILENAME`创建文件TEST，并将选定行写入;
- `:r FILENAME`检索文件FILENAME并将其放在光标处的下一行;
- `:r !ls`读取ls命令的输出，并将其放在光标处的下一行;
---
### Lesson 6
- `o`在光标下方打开一行;（置于插入模式）
- `O`在光标上方打开一行;（置于插入模式）
- `a`在光标后方插入文本;（置于插入模式）
- `A`在行尾插入文本;（置于插入模式）
> `y`运算符复制(yanks)文本，`p`粘贴(puts)文本;
>- `yw`拉拽一个单词,`yy`拉拽整行;
- `R`进入替换(Replace)模式，直到按下`<ESC>`;
> 输入`:set xxx`设置选项"xxx"，一些选项（任选长或短选项名称）是：
>- `ic` `ignorecase`	在搜索时忽略大小写;
>- `is` `incsearch` 	在搜索时显示短语的部分匹配;
>- `hls` `hlsearch` 	在搜索时高亮显示所有匹配短语;
>- 前置`no`关闭一个选项，如`:set noic nois`;
>- 如果只想忽略一个搜索命令的大小写，可以在短语中使用`\c`，即`/ignore\c <ENTER>`;
---
### Lesson 7
- `:help`或`<F1>`或`<HELP>`打开帮助窗口;
- `:help cmd`查找cmd上的帮助;
- `<CTRL-W><CTRL-W>`跳转窗口;
- `:q`关闭帮助窗口;
> 创建vimrc启动脚本保留首选设置;
>- `:e /.vimrc`;
>- 阅读示例vimrc文件内容，`:r $VIMRUNTIME/vimrc_example.vim`;
>- `:w`写文件;
- 键入`:`命令时，按下`<CTRL-D>`查看可能的补全，按`<TAB>`使用补全;（确保Vim不处于兼容模式(not in compatible mode)`:set nocp`）
