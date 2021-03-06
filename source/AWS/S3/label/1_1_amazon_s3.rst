======================================
스토리지 클래스
======================================

------------------------
1) 스토리지 클래스
------------------------

S3는 여러 방면의 스토리지 클래스를 제공한다. 예를 들어 자주 액세스하기 위해 미션 크리티컬한 데이터를 S3 Standard에 저장하고,
액세스 빈도가 낮은 데이터를 S3 Standard-IA 또는 S3 One Zone-IA에 저장하여 비용을 절감할 수 있다.

- **범용**

  : Amazon S3 Standard(S3 Standard)

  자주 액세스하는 데이터를 위해 높은 내구성, 가용성 및 성능을 갖춘 객체 스토리지를 제공한다.

  짧은 지연 시간과 많은 처리량을 제공하므로 클라우드 애플리케이션, 동적 웹 사이트, 콘텐츠 배포, 모바일 및 게임 애플리케이션, 빅데이터 분석 등의 다양한 사용 사례에 적합하다.

- **간헐적**

  : Amazon S3 Intelligent-Tiering(S3 Intelligent-Tiering)

  데이터 액세스 패턴 변경 시 가장 효율적인 액세스 계층으로 데이터를 자동으로 이동하여 성능에 대한 영향 또는 추가비용 없이 자동으로 스토리지 비용을 절감한다.

  S3 Intelligent-Tiering은 범용 액세스와 간헐적인 액세스에 최적화된 액세스 티어와 비동기 액세스용으로 설계된 2개의 아카이브 액세스 티어에 객체를 저장하는 방식으로 작동한다.

  **객체가 저장되는 곳**

  - 업로드 시

    => Frequent Access 계층에 자동 저장

  - 30일간 액세스 되지 않았을 경우

    => Infrequent Access 계층에 자동으로 이전

  - 90일 연속 액세스 되지 않았을 경우

    => Archive Access 계층에 자동으로 이전

  - 180일 연속 액세스 되지 않았을 경우

    => Deep Archive Access 계층에 자동으로 이전한다.

- **드문 액세스**

  - : Amazon S3 Stardard-Infrequent Access(S3 Standard-IA)

    S3 Standard-IA는 자주 액세스하지 않지만 필요할 때 빠르게 액세스해야 하는 데이터에 적합하다. ( 밀리초 단위 액세스 성능 )

    S3 Standard-IA는 Standard 클래스(0.023~0.021/GB) 보다 절반가량 저렴한 스토리지 요금(0.0125/GB)으로 제공하지만
    검색 요금이 발생한다(0.01/GB).

  - : Amazon S3 One Zone - Infrequent Access(S3 One Zone-IA)

    최소 3개의 가용 영역의 데이터를 저장하는 다른 S3 스토리지 클래스와는 달리, 단일 AZ에 데이터를 저장하며 비용이 S3 Standard-IA보다 20% 가량 적게 든다.

- **아카이빙**

  S3 Glacier 및 S3 Glacier Deep Arachive는 저비용 데이터 보관을 위해 설계된 스토리지 클래스이다.

  - Amazon S3 Glacier(S3 Glacier)

    : 분 단위로 데이터의 일부를 검색해야 하는 아카이빙에 사용한다. 최소 스토리지 기간이 90일이며 그 전에 데이터를 삭제 및 덮어쓰기, 이전할 경우 90일 요금이 부과된다.
    최소 1분 ~ 5분 이내에 액세스할 수 있다.

  - Amazon S3 Glarier Deep Archive(S3 Glacier Deep Archive)

    : 거의 액세스할 필요가 없는 데이터를 보관할 때 사용한다. 최소 스토리지 기간은 180일이고 기본 검색 시간은 12시간이다.
