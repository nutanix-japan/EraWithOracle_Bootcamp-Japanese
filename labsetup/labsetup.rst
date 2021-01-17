.. _labsetup:

----------------------
Oracleのラボセットアップ
----------------------

データベースブートキャンプにようこそ！
このブートキャンプではなぜNutanixがワークロードに理想的なプラットフォームなのかを体験して頂きます。

今までのSANベースのアーキテクチャがもたらすパフォーマンスへの影響や従来の仮想化スタックの高コストによりOracleを仮想化することは課題になっていました。
企業やIT部門は、コスト、運用のシンプルさ、一貫した予測可能なパフォーマンスのバランスをとるために議論してきました。

Nutanix Enterprise Cloudはこれらの課題を解決し、Oracleのようなビジネルクリティカルな仮想化アプリケーションを容易に実現します。
Acropolis Distributed Storage Fabric(DSF)はSANエンタープライズに期待されるような機能を提供するソフトウェアで定義されたソリューションです。
特に、OracleはDSFの機能から恩恵を受けています。

- ローカライズされたI/Oと、インデックスとキーデータベースファイルのフラッシュの使用により、操作のレイテンシを短縮します。
- ランダムワークロードとシーケンシャルワークロードの両方を処理できる高度に分散されたアプローチ。
- システムのダウンタイムやパフォーマンスに影響を与えることなく、新しいノードを追加してインフラストラクチャをスケーリングします。
- バックアップ操作とビジネス継続性プロセスを簡素化するNutanixデータ保護と災害復旧ワークフロー。

ビジネスの肝になるアプリケーションのホスティングのための一般的なインフラの課題を解決するために、Nutanixはデータベース管理に関連する多くのペインポイントに対処しようとしています。

.. figure:: images/4.png

従業員数1,000人以上の北米企業500社の2018年IDC調査をもとに試算したところ…:

- 組織の77％が本番環境に200を超えるデータベースインスタンスを持っている
- 82％が各DBのコピーを10個以上持っている
- 総ストレージ容量の45％〜60％は、コピーデータの格納専用です。
- データベースクローンの32％は、開発/テストの分析のために毎日の更新が必要です
- データをコピーすると、IT組織は2020年に556.3億ドルの費用がかかる

現状を鑑みると、このままではストレージの利用効率と管理者の時間の両方にとって悪影響をもたらします。そのため、Nutanix Eraが必要になるわけです。

.. figure:: images/5.png

Nutanix Era はエンタープライズ向けのクラウドのDBaaSを提供します。
Nutanix Enterprise Cloud OSによって、データや処理能力に対して最大限の優位性を得ることができます。
Nutanix Eraはマルチプルデータベースエンジンによって、一般的なAPIのもたらすデータベース操作の複雑さをカバーし、CLIやコンシューマーグレードのGUIの体験を提供します。
また、複製などのデータベース操作をより効率的にし、お客様のTCOを軽減させます。


..  プロジェクトの形成
  +++++++++++++++++++++

    このラボでは前に構築したCalm Blueprintsを利用してアプリケーションの提供を試みます。

  #. **Prism Central** 内で、:fa:`bars` **> Services > Calm** を選択します。

  #. 左側のメニューから **Projects** を選択し、**+ Create Project** をクリックます。

     .. figure:: images/2.png

  #. 以下の項目を埋めてください。

     - **Project Name** - *Initials*\ -Project
     - Under **Users, Groups, and Roles**, select **+ User**
        - **Name** - Administrators
        - **Role** - Project Admin
        - **Action** - Save
     - Under **Infrastructure**, select **Select Provider > Nutanix**
     - Click **Select Clusters & Subnets**
     - Select *Your Assigned Cluster*
     - Under **Subnets**, select **Primary**, **Secondary**, and click **Confirm**
     - Mark **Primary** as the default network by clicking the :fa:`star`

     .. figure:: images/3.png

  #. **Save & Configure Environment** をクリックします。

.. Windows Tools VMの展開
.. ++++++++++++++++++++++++++++
..
.. このラボでのエクササイズのいくつかはWindows Tools VMに依存します。以下の手順に従ってディスクイメージから個人のVMを展開してください。
..
.. #. **Prism Central** 内で:fa:`bars` **> Virtual Infrastructure > VMs** を選択します。
..
.. #. **+ Create VM** をクリックします。
..
.. #. 以下の項目を埋めてください。
..
..    - **Name** - *Initials*\ -WinToolsVM
..    - **Description** - Manually deployed Tools VM
..    - **vCPU(s)** - 2
..    - **Number of Cores per vCPU** - 1
..    - **Memory** - 4 GiB
..
..    - Select **+ Add New Disk**
..       - **Type** - DISK
..       - **Operation** - Clone from Image Service
..       - **Image** - WinToolsVM.qcow2
..       - Select **Add**
..
..    - Select **Add New NIC**
..       - **VLAN Name** - Secondary
..       - Select **Add**
..
.. #. **Save** をクリックしてVMを作成します。
..
.. #. *Initials*\ **-WinToolsVM** を起動します。
