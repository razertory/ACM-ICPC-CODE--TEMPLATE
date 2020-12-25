# 字符串

## KMP

> 在计算机科学中，Knuth-Morris-Pratt 字符串查找算法（简称为 KMP 算法）可在一个主文本字符串 S 内查找一个词 W 的 出现位置。此算法通过运用对这个词在不匹配时本身就包含足够的信息来确定下一个匹配将在哪里开始的发现，从而避免重新检查先前匹配的字符。

```java
// Partial Match Table
int[] preKmp(char[] ws) {
    int[] pre = new int[ws.length)];
    int i = 0, j = -1; pre[0] = -1;
    while (i < ws.length) {
        while (j != -1 && ws[i] != ws[j]) {
            j = pre[j];
        }
        pre[++i] = ++j;
    }
    return pre;
}

// 移动位数 = 已匹配的字符数 - 对应的部分匹配值
int kmpCount(char[] pattern, char[] ws) {
    int i = 0, j = 0, count = 0;
    int[] pre = preKmp(ws);
    while (i < ws.length) {
        while ( j != -1 && ws[i] != ws[j]) {
            j = pre[j];
        }
        j++; j++;
        if (j >= pattern.length) {
            count++;
            j = pre[j];
        }
    }
    return count;
}

```