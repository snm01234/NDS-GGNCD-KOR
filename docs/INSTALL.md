# 한글 패치 1.0.0 적용 안내

## 준비할 파일

- 수정하지 않은 일본판 『SD Gundam G Generation: Cross Drive』 ROM
- 배포 ZIP에 들어 있는 `SDGG_CrossDrive_Korean_v1.0.0.xdelta`
- xdelta3 형식 패치를 적용할 수 있는 도구

배포 파일 이름은 `SDGG_CrossDrive_Korean_v1.0.0.zip`입니다. xdelta3 실행 파일은 포함되어 있지 않습니다. 명령줄 도구가 필요하면 [공식 xdelta3 3.1.0 배포 페이지](https://github.com/jmacd/xdelta-gpl/releases/tag/v3.1.0)를 참고할 수 있습니다.

## 원본 확인

파일 이름만으로 원본 일치 여부를 판단하지 말고 크기와 해시를 확인해 주세요.

| 항목 | 값 |
|---|---|
| 파일 이름 예 | `1285 - SD Gundam G Generation - Cross Drive (Japan).nds` |
| 크기 | 134,217,728바이트 · 128 MiB |
| CRC32 | `066C9B38` |
| SHA-1 | `c88ba4c0d05b15432cce63d9ece47afe5a0615c3` |
| SHA-256 | `9435f495524d0a6ffcee624b5b7ce952938c1edd57785f1a1b476e255ff948a3` |

이전 한글 패치판이나 내용이 달라진 ROM을 원본 파일로 지정하지 않습니다.

## 패치 적용

패치 도구에서 원본 파일, 패치 파일, 새 출력 파일을 각각 지정합니다. 출력 이름의 예는 `SDGG_CrossDrive_Korean_v1.0.0.nds`입니다. 원본과 다른 파일 이름으로 저장합니다.

xdelta3 명령줄 예시는 다음과 같습니다. 각 파일이 있는 폴더에서 실행하거나 파일 이름 대신 실제 경로를 사용하세요.

```text
xdelta3 -d -s "1285 - SD Gundam G Generation - Cross Drive (Japan).nds" "SDGG_CrossDrive_Korean_v1.0.0.xdelta" "SDGG_CrossDrive_Korean_v1.0.0.nds"
```

파일 이름을 다르게 정했어도 내용과 해시가 같으면 동일한 적용 결과입니다.

## 결과 확인

| 항목 | 값 |
|---|---|
| 크기 | 134,217,728바이트 · 128 MiB |
| CRC32 | `F1436ADF` |
| SHA-1 | `46fef0addeea2c527d3ce40562cdcd48051db2e3` |
| SHA-256 | `45f1dbb2a5bef5b902618ecc1c3a9ee2d8969c3388031a75476d877935596b36` |

이번 1.0.0의 결과는 v071과 바이트 단위로 동일합니다. 버전과 파일 이름은 기존 v069 기준 배포본과 같지만 해시가 바뀌었으므로, 위의 결과 해시와 현재 배포 파일의 확인 값을 사용하세요. 갱신본도 수정하지 않은 일본판 원본에 적용합니다. 패치와 ZIP의 무결성은 [배포 파일 SHA-256](../SHA256SUMS_RELEASE.txt)으로 확인할 수 있습니다. [배포 명세](../release_manifest.json)에는 원본·결과·패치의 해시가, 패치 ZIP 안의 `SHA256SUMS.txt`에는 포함 파일별 해시가 들어 있습니다.

## 저장 파일

기존 배터리 저장 파일을 먼저 백업하고, 사용하는 에뮬레이터의 저장 폴더와 이름 규칙에 맞춰 새 ROM 이름으로 복사합니다. 예를 들어 ROM 이름을 `SDGG_CrossDrive_Korean_v1.0.0.nds`로 사용한다면 DeSmuME에서는 같은 기본 이름의 `.dsv` 파일을 사용합니다.

ROM을 새로 실행한 다음 게임 안의 불러오기로 진행 상태를 확인하세요. savestate는 이전 ROM의 메모리와 화면 데이터를 포함하므로, 새 패치에서도 이전 문구나 이미지가 다시 보일 수 있습니다.

## 적용이 안 되거나 예전 화면이 보일 때

1. 원본의 크기와 SHA-256이 위 값과 일치하는지 확인합니다.
2. 원본 파일에 다른 패치를 먼저 적용하지 않았는지 확인합니다.
3. 출력 파일을 새로 실행하고 있는지 확인합니다.
4. 이전 savestate 대신 게임 안의 일반 저장을 불러옵니다.
5. 문제가 계속되면 패치·실행 환경 버전과 재현 위치를 함께 제보합니다.
