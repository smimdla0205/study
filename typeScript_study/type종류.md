## 타입 종류

```typescript
let uname: string; // 문자열 타입
let age: number; // 숫자 타입
let isStudent: boolean; // 불리언 타입
let hobbies: string[]; // 문자열 배열 타입
let n: null; // null 타입
let u: undefined; // undefined 타입
let numbers: number[] = [1, 2, 3];
let numbers: Array<number> = [1, 2, 3];
let matrix: number[][] = [
  [1, 2, 3],
  [4, 5, 6],
];
let users: object; // 객체 타입
let user: { name: string; age: string }; // 객체 타입

let fuc: () => void;
function message(message: string): void {
  console.log(message);
}

let sym1: symbol = Symbol("sym");
let sym2: symbol = Symbol("sym");
console.log(sym1); // Symbol(sym)
console.log(sym1 === sym2); // false, 각 심볼은 고유함
```

### Symbol

- 심볼(Symbol)은 자바스크립트의 고유하고 변경할 수 없는 데이터 타입으로, 주로 객체의 속성 키를 유일하게 만들기 위해 사용됩니다.

## 구조적 타입 종류

- 구조적 타입이란? 타입 시스템에서 객체의 구조(속성 및 그 속성의 타입)에 따라 타입을 정의하고 비교하는 방식입니다.

1. 객체 타입

```typescript
let user2: { name: string; age: string }; // 객체 타입
let user3: object; // 객체 타입
```

2. 튜플 타입

```typescript
let point: [string, number] = ["이십", 20];
```

3. 함수 타입

```typescript
let fuc1: (name: string) => string;
let fuc2: () => void; // void 타입
function message(message: string): void {
  console.log(message);
}
```

4. Interface, type

```typescript
interface Person {
  name: string;
  age: number;
}
type Person = {
  name: string;
  age: number;
};
```

5. Union 타입

- or 또는 과 같은 역할을 하며,| 연산자를 사용하여 결합합니다. 변수나 매개변수가 여러 타입 중 하나를 가질 수 있도록 정의.

```typescript
type ID = number | string;
```

6. 교차 타입

- & 연산자를 사용하여 결합합니다. 여러 타입을 결합하여 하나의 새로운 타입을 생성합니다.

```typescript
type Address = {
  street: string;
  city: string;
};

type Person = {
  name: string;
  age: number;
};

type PersonWithAddress = Person & Address;

let person: PersonWithAddress = {
  name: "Alice",
  age: 30,
  street: "123 Main St",
  city: "Wonderland",
};
```

7. 리터널 타입

```typescript
let dir: "left" | "right";
```

- 리터럴 타입은 특정 값만을 허용하는 타입을 정의하는 것입니다

8. 제너릭 타입

```typescript
type Box<T> = {
  value: T;
};

let numberBox: Box<number> = { value: 123 };
let stringBox: Box<string> = { value: "hello" };
```

## 타입스크립에만 있는 타입

1. any

- any 타입은 모든 타입의 값을 허용합니다

2. unknown

- unknown 타입은 any와 비슷하지만, unknown 타입의 값에 대해 타입 검사를 수행하기 전까지는 어떤 연산도 수행할 수 없습니다.

- ex/ try catch 문에서 자주 사용

```typescript
const a: unknown = "hello";
const b: unknown = "world";
a + b; // 에러처리
```

3. void

- void는 함수가 반환값이 없음을 명시합니다.

4. {}

- {} 타입은 빈 객체 타입을 의미하지만, object는 객체가 아닌 값도 포함할 수 있습니다.

5. never

- never 타입은 결코 발생하지 않는 값을 나타냅니다.

- ex/ 함수가 절대 반환하지 않거나, 무한 루프를 돌거나, 오류를 던지는 경우에 사용됩니다.
