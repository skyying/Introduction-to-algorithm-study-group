

## 2.1-1

Using Figure 2.2 as a model, illustrate the operation of INSERTION-SORT on the array A =  {31, 41, 59, 26, 41, 58}


```
round 1: 
current = 41
31, 41, 59, 26, 41, 58

round 2:
current = 59
31, 41, 59, 26, 41, 58

round 3:
current = 26
_, 31, 41, 59, 41, 58 
26, 31, 41, 59, 41, 58

round 4:
current = 41
26, 31, 41, _, 59, 58
26, 31, 41, 41,59, 58

round 5:
current = 58
26, 31, 41, 41, _, 59
26, 31, 41, 41, 58, 59
```



## 2.1-2

Rewrite the INSERTION-SORT procedure to sort into nonincreasing instead of nondecreasing
order.

```javascript
function insertionSort(arr){
    for(let i = 1; i < arr.length; i++){
        let current = arr[i];
        let j = i - 1;
        // just flip greater than or less than sign
        while( j >= 0 && arr[j] < current){
            arr[j+1] = arr[j];
            j--;
        }
        arr[j+1] = current;
    }
    return arr;
}
```

```python
def insertionSort(arr):
    for i in range(1, len(arr)):
        current = arr[i]
        j = i - 1;
        while j >= 0 and arr[j] < current:
            arr[ j + 1 ] = arr[j]
            j = j - 1;
        arr[ j + 1 ] = current
    return arr
```


## 2.1-3

Consider the searching problem:
Input: A sequence of n numbers A = ⟨a1,a2,...,an⟩ and a value v.
Output: An index i such that v = A[i] or the special value NIL if v does not appear in A.
Write pseudocode for linear search, which scans through the sequence, looking for v. Using a loop invariant, prove that your algorithm is correct. Make sure that your loop invariant fulfills the three necessary properties.

```python

def isValue(A, x):
	for element in A:
	    if element == x:
	    	return True
	return False

```


## 2.1-4

Consider the problem of adding two n-bit binary integers, stored in two n-element
arrays A and B. The sum of the two integers should be stored in binary form in
an ( n +1 )-element array C. State the problem formally and write pseudocode for
adding the two integers.


```javascript
@param a [1, 0, 1, 0]
@param b [0, 1, 1, 1]
@return c [1, 0, 0, 0, 1]
function addTwoBinaryInteger(a, b){
    let carry = 0;
    let c = [];
    for(let i = a.length-1; i >= 0; i--){
        let sum = a[i] + b[i] + carry;
        c[i] = sum % 2;
        carry = Math.floor(sum / 2);
    }
    return carry > 0 ? [1, ...c] : c;
}

```

```python

def addTwoBinaryInteger(a, b):
    carry = 0
    c = [0 for i in range(len(a))]
    for i in range(len(a) - 1, -1, -1):
        sum = a[i] + b[i] + carry
        c[i] = sum % 2
        carry = sum // 2
    if carry > 0:
       return [1] + c
    return c

addTwoBinaryInteger([1, 1, 1], [1, 1, 1]) // [1, 1, 1, 0]

```