# Kory Parser

HWP·HWPX·HWPML, PDF, DOCX·PPTX·XLS·XLSX와 이미지에서 문단·표·목록과 원문 위치를
추출하는 Python 라이브러리다. Python 3.11 이상을 지원한다.

## 설치

PyPI에는 아직 게시하지 않았다. GitHub 소스에서 설치한다.

```bash
pip install "git+https://github.com/styglab/kory-parser.git"
```

소스를 직접 내려받아 설치할 수도 있다.

```bash
git clone https://github.com/styglab/kory-parser.git
cd kory-parser
pip install .
# OCR이 필요할 때
pip install '.[ocr]'
```

## 사용

```python
from kory_parser import ParseOptions, parse

result = parse("document.hwpx", ParseOptions(ocr=False))
if not result.success:
    raise ValueError(result.error_code)
native_json = result.to_dict()
markdown = result.markdown
```

```bash
kory-parser document.hwpx -o parsed.json
```

문서 생성·편집·렌더링은 지원하지 않는다. 임의 문서의 정확도를 보장하지 않으며
진단 코드와 원문 근거를 함께 확인해야 한다. OCR은 선택 기능이다.

- [설치·옵션·지원 범위와 제한](docs/usage.md)
- [변경 이력](docs/change_history.md)
- [라이선스 전문](LICENSE) · [원저작권·의존성 고지](NOTICE)

현재 배포 라이선스는 AGPL-3.0-or-later다. 원저작권 고지와 의존성별 라이선스를 유지한다.
평가·회귀 테스트·벤치마크·Codex 개선 실행기는 이 라이브러리의 배포 범위에 포함하지 않는다.
