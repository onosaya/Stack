# Stack
スタック

public class Stack {
	private int max; // スタックの容量
	private int ptr; // スタックポインタ
	private int[] stk; // スタックの本体
	
	public class EmptyIntStackException extends RuntimeException { // スタックが空
		public EmptyIntStackException() { }
	}
	
	public class OverflowIntStackException extends RuntimeException { // スタックが満杯
		public OverflowIntStackException() { }
	}
	
	public Stack(int capacity) {
		ptr = 0;
		max = capacity;
		try {
			stk = new int[max]; // スタック生成
		} catch (OutOfMemoryError e) {
			max = 0;
		}
	}
	
	public int push(int x) throws OverflowIntStackException {
		if (ptr >= max)
			throw new OverflowIntStackException();
		return stk[ptr++] = x;
	}
	
	public int pop() throws EmptyIntStackException {
		if (ptr <= 0)
			throw new EmptyIntStackException();
		return stk[‐‐ptr];
	}
	
	public int peek() throws EmptyIntStackException {
		if (ptr <= 0)
			throw new EmptyIntStackException();
		return stk[ptr ‐ 1];
	}
	
	public int indexOf(int x) { // スタックの探索
		for (int i = ptr ‐ 1; i >= 0; i‐‐)
			if (stk[i] == x)
				return i; // 探索成功
		return ‐1; // 探索失敗
	}
	
	public void clear() {
		ptr = 0;
	}
	
	public int capacity() {
		return max;
	}
	
	public int size() {
		return ptr;
	}
	
	public boolean isEmpty() {
		return ptr <= 0;
	}
	
	public boolean isFull() {
		return ptr >= max;
	}
	
	public void dump() {
		if (ptr <= 0)
			System.out.println("空です．");
		else {
			for (int i = 0; i < ptr; i++)
				System.out.print(stk[i] + " ");
			System.out.println();
		}
	}
}
