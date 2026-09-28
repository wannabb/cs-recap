relational model

definition: relation + constraints

constraints
  - domain
  - Key
  - Entity integrity
  - referential integrity

  1) Domain constraints
    - `atomic attribute` in domain value, allow `NULL` value
    > [!MEMO] 
    > atomic <=> composite attribute

  2) Key constraints
    - Super key and Candidate key
    > super key = set of unique attributes 
    > candidate key = set of unique and essential attributes (minimal unique set)
    - PK(primary key) = d ( d ∈ candidate key )
  3) Entity integrity constraints
    - PK = unique & not `NULL`
  4) Referential integrity constraints
    - FK: (refer retrieved PK) or (null)
    > [!CAUTION]
    > 참조하려는 값이 포함된 테이블은 이전에 생성되어 있어야 함.

3. ER-to-Relational Model
  1) Strong entity types: 각 엔티티에 대응되는 릴레이션 R 생성(테이블 생성), 각 attribute를 R의 속성으로 포함시키고 composite attribute는 하위 속성들을 포함시킨다. multivalued는 추후 고려하도록 한다. 캔디데이트 키 중 하나를 PK로 선정한다. 만약 composite가 PK가 될 경우 하위 속성들의 조합이 R의 기본키가 된다. attribute의 이름은 고유하게 바꾸자(table_name + 기존 속성이름 추천).
  2) Weak entity types: 자신만의 PK를 갖추지 못해 소유(Strong) entity의 PK를 FK로 참조하며, [FK + 자신의 부분키(Partial Key)] 조합을 복합 기본키(PK)로 사용하여 식별되는 엔티티.
  3) Binary 1:N relation types: N쪽이 되는 엔티티 릴레이션에 1쪽의 PK를 FK로 덧붙이고, 관계 자체의 속성도 N쪽에 포함시킴.
  4) Binary 1:1 relation types: 엔티티 T와 S가 있고 관계 RS가 있다면 한쪽 릴레이션에 반대쪽의 PK를 FK로 붙이고 관계의 속성도 추가함. (보통 필수 참여(Total Participation)하는 쪽에 FK를 넣는 것이 NULL 발생을 줄이고 메모리 효율성이 높음)
  5) Binary M:N relation types: 관계 RS에 대응되는 새로운 릴레이션 RS1을 생성. RS에 속하는 모든 simple attributes를 RS1에 포함시키고, 참여하는 두 엔티티의 PK를 FK로 가져와 이 FK들의 조합을 RS1의 기본키(PK)로 지정함.
  6) N-ary relation types: 하나의 관계에 3개 이상의 엔티티가 참여하는 타입. 관계 RS 자체의 simple attributes와 참여하는 모든 엔티티의 PK(외래키)를 포함하는 새로운 릴레이션 RS1을 생성함. 기본적으로 모든 FK의 조합이 RS1의 기본키(PK)가 되나, 관계 대응수(카디널리티)가 1인 엔티티의 외래키는 기본키 조합에서 제외함.
  7) Multivalued attributes: 하나의 속성이 여러 개의 값을 가질 수 있는 경우(1NF 위반 방지). 멀티밸류드 어트리뷰트 MA에 대해 별도 릴레이션 R 생성. MA의 속성 A를 R에 포함시키고 소유 엔티티의 기본키를 R의 FK로 포함시킴. [FK + A]의 조합이 R의 기본키(PK)가 됨.
