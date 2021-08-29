# Vue

## Project setup
```
npm install
```

### Compiles and hot-reloads for development
```
npm run serve
```

### Compiles and minifies for production
```
npm run build
```

### Lints and fixes files
```
npm run lint
```

### Customize configuration
See [Configuration Reference](https://cli.vuejs.org/config/).

----
### 데이터 바인딩
데이터를 변수에 저장해놓고 html에 {{변수}}를 쓰면, 변수에 해당하는 데이터를 넣어준다.     
데이터 값이 변경되면 자동으로 업데이트 된다.   
* 사용 방법   
기본 형태 : ```{{변수}}```    
html 속성에서 변수를 사용하려고 할 때 : ```:속성 = "데이터 이름"```
* 변수에 데이터 저장하는 방법   
아래와 같이 data의 중괄호 안 return에 저장할 변수를 오브젝트(```변수명 : 값```)자료로 저장해둔다.
```
export default {
  name: 'App',
  data() {
    return {
      // 데이터 보관함, 변수 저장
      price1 : 60,
      price2 : 70,
      products : ['역삼동 원룸', '천호동원룸', '마포구원룸']
    }
  },
  components: {
    
  }
}
```
### 반복문
```v-for="변수 in 범위" :key = "계속 변하는 숫자 또는 문자"```   
* 예시
```
<div class="menu">
    <a v-for="headerMenu in headerMenus" :key = "headerMenu">{{headerMenu}}</a> 
  </div>
```
```
headerMenus : ['Home', 'Shop', 'About']
```
위 예시에서 headerMenu 변수에는 headerMenus의 원소들이 차례대로 대입된다.       
따라서 Home, Shop, About 3개의 a태그가 만들어진다.
### 조건문
`v-if="조건"` : 조건이 true일 때만 해당 컴포넌트가 화면에 보인다.
* 예 : `v-if="_loginState == 0"`
* 예시 코드 (로그인 상태에 따라 헤더에 보여지는 메뉴가 달라지도록 설정)
```
<div class="nav-menu">
    <router-link class="menu" v-if="_loginState == 0" :to="{name : 'Signup'}">Sign up</router-link>
    <img class="nav-menu-division" v-if="_loginState == 0" src="../../assets/nav-menu-division.svg" alt="">
    <button class="menu" @click="openLoginPopup" v-if="_loginState == 0">Login</button>
    <button class="menu" @click="openLoginPopup" v-if="_loginState == undefined">Login</button>
    <button class="menu" @click="logout" v-if="_loginState == 1">Logout</button>
    <img class="nav-menu-division" v-if="_loginState == 1" src="../../assets/nav-menu-division.svg" alt="">
    <!-- 로그인이 된 경우 마이페이지로 이동 -->
    <router-link class="menu" :to="{name : 'Mypage'}" v-if="_loginState == 1">My page</router-link>
</div>
```
