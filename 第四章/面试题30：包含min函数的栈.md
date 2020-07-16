# 面试题30：包含min函数的栈

## 题目
定义栈的数据结构，请在该类型中实现一个能够得到栈的最小元素的min函数。在该栈中，调用min、push、以及pop的时间复杂度都是O(1)。

## 方法
准备一个辅助栈，每次都把最小的元素（之前的最小元素和新压入栈的元素二者的较小值）都保存在这个辅助栈里。

这样就能保证辅助栈的栈顶一直都是最小元素。当最小元素从数据栈内被弹出后，同时弹出辅助栈的栈顶元素，此时辅助栈的新栈顶元素就是下一个最小值。

## 代码
```java
class MinStack {
    private Stack<Integer> datastack;
    private Stack<Integer> minstack;

    public MinStack() {
        datastack = new Stack<>();
        minstack = new Stack<>();
    }
    
    public void push(int x) {
        datastack.push(x);
        minstack.push(minstack.isEmpty()? x: Math.min(minstack.peek(), x));
    }
    
    public void pop() {
        datastack.pop();
        minstack.pop();
    }
    
    public int top() {
        return datastack.peek();
    }
    
    public int min() {
        return minstack.peek();
    }
}
```
