## 主訴表現（Chief Complaint ; cc）

以下の２種類の身体的主訴表現に `cc` タグを適用する．

1. 身体症状・異常（例：「痛い」, 「ふわふわ」, 「変な感じ」）
2. 身体症状の結果としての苦痛表現 （例：「つらい」, 「しんどい」）

※「ふわふわ」「ズキズキ」のような擬音語も主訴として扱う  
※ cc・changeはともに「～感じ」という表現では「感じ」を含めてアノテーションする  

<br>

###  cc_positive
症状ありの場合，属性 `p` を適用する  
<br>
＜アノテーション例＞
```xml
(1) <cc_p>めまい</cc_p>がします。
(2) <feature>少し</feature> <cc_p>ふらっと</cc_p>するかな。
```
<br>  

###  cc_negative
症状なしの場合，属性 `n` を適用する
```xml
(1) <cc_n>痛く</cc_n>ない
(2) <cc_n>大丈夫</cc_n>
```


<br>


## 変化（change）

症状の変化表現（1：好転，2：悪化，3：継続）に `change` を適用する

```xml
(1a) <time_cc>今</time_cc>は<feature>だいぶ</feature> <change>楽になっています</change>。
(1b) <cc_p>痛み</cc_p>も<time_cc>昨日</time_cc>より<change>落ち着いている</change>

(2a) <feature>全然</feature><change>良くならない</change>
(2b) <cc_p>熱</cc_p>がなかなか<change>下がらなくて</change><cc_p>熱い</cc_p>

(3a) <cc_negative>大丈夫</cc_negative>、<change>変わりない</change>です。
(3b) <body>右手</body>の<cc_p>動かしにくさ</cc_p><change>残ってます</change>。
```

<br>  


## 身体部位（body）

解剖学的部位と症状の発症部位に `body` を適用する  

```xml
(1) なんか<body>腰</body>が<cc_p>痛い</cc_p>。
(2) <body>傷のところ</body>が<cc_p>痛い</cc_p>です。
```

<br>  


## 頻度（freq）

症状の頻度表現に `freq` を適用する

```xml
(1) <freq>常に</freq><cc_p>痛い感じ</cc_p>で。
(2) <freq>また</freq><cc_p>熱</cc_p>がでてきちゃったね。
(3) <freq>よく</freq><t-key>トイレ</t-key>で<cc_p>起きちゃう</cc_p>ね。
```

<br>  


## 特徴・尺度（feature）
症状の特徴や尺度に `feature` を適用する  
※ペインスケール（痛みの強さの数値尺度）は `t-val` を適用する

```xml
(1) <cc_n>痛み</cc_n>は<feature>ほとんどない</feature>ですね
(2) <feature>我慢してた</feature>けど治らないから呼びました。
(3) <cc_p>痛み</cc_p>はあるけど、<feature>我慢できる</feature>範囲内です。
```

「ほとんど痛みはない」の場合は `<feature>ほとんど</feature> <cc_n>痛み</cc_n> はない` 


<br>  


## 看護観察項目・結果（t-key, t-val）

ペインスケール・食欲・喀痰・排尿・排便・検査項目と結果（血糖値や血圧値など）に `t-key`（項目名）, `t-val`（値） を適用する

```xml
(1) <cc_p>咳</cc_p>が出て<t-key>痰</t-key>が<t-val>出そう</t-val>で<t-val>出ない</t-val>。
(2) <t-key>血糖</t-key>測ったら、<t-val>６０</t-val>でした。
```


<br>  


## 経過表現（time）
以下の 4 種類の時間経過表現に `time` を適用する
1. 症状・看護観察項目に関する時間経過表現（time_cc）
2. シチュエーション（time_s）
3. 既往（time_past）
4. 症状以外の時間表現（time_other）

<br>

###  time_cc
症状・看護観察項目に関する時間・変化表現に属性 `cc` を適用する

```xml
(1) <time_cc>朝方</time_cc><feature>ちょっと</feature><cc_p>吐いちゃいました</cc_p>
(2) <t-key>痰</t-key><time_cc>なかなか</time_cc><t-val>出なくて</t-val><cc_p>苦しい感じ</cc_p>がする。
(3) <time_cc>段々</time_cc><cc_p>痛く</cc_p>なってきました
(4) <cc_p>痛み</cc_p>も<time_cc>昨日より</time_cc><change>落ち着いている</change>
```
<br>

###  time_s
「～とき」，「～したら」，「～しなければ」（＋これらに変換可能な表現）のようなシチュエーション表現に属性 `s` を適用する

```xml
(1) <time_s>ご飯食べる時</time_s>に<body>上の歯</body>が<cc_p>痛む</cc_p>
(2) <time_s>眠ろうと思ったんだけど</time_s>、<feature>なかなか</feature><cc_p>眠れなくて</cc_p>
(3) <time_s>飲み込むのが</time_s><cc_p>痛くて辛い</cc_p>
(4) <time_s>管がとれて</time_s><change>スッキリ</change>しました。
```

<br>

###  time_past
過去症状に関する記述の時間表現に `past` を適用する

```xml
(1) <time_past>前も</time_past><cc_p>詰まった</cc_p>ことがあります。
(2) <time_past>もともと</time_past><cc_p>便秘</cc_p>だった。
(3) <time_past>今まで</time_past>は<t-val>１日１回</t-val>ありました。　
```

<br>

###  time_other
症状以外の時間表現に `other` を適用する

```xml
(1) <time_other>今</time_other>何時ですか？<cc_p>眠れません</cc_p>。
(2) <time_other>今日</time_other>は<time_other>まだ</time_other>使ってなくて...
```
